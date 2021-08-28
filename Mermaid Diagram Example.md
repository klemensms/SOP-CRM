
``` mermaid
stateDiagram %%comment
  s1
  state "Description with parenthesis" as s2
  s3 : Description with colon

  s1 --> s2
  s2 --> s3: Colon transition
  [*] --> s1 : Transition text
  s3 --> [*]

  state NestedComposite {
      [*] --> Nested

      state Nested {
          [*] --> second
      }
  }

  %% comment here
  state fork_state <<fork>>
      [*] --> fork_state
      fork_state --> State2

      state join_state <<join>>
      State2 --> join_state

  note right of State1
    Important information! You can write
    notes.
  end note
  note left of State2 : This is the note to the left.

  %% concurrency
  state Active {
      [*] --> NumLockOff
      NumLockOff --> NumLockOn : EvNumLockPressed
      NumLockOn --> NumLockOff : EvNumLockPressed
      --
      [*] --> CapsLockOff
      CapsLockOff --> CapsLockOn : EvCapsLockPressed
      CapsLockOn --> CapsLockOff : EvCapsLockPressed
  }
```


```mermaid
sequenceDiagram %% diagram
  autonumber
  %% participant
  participant Alice
  participant B as Bob<br>Newline
  participant C as Carol
  %% arrows
  B->C: Solid line without arrow
  B-->C: Dotted line without arrow
  B->>C:Solid line with arrowhead
  B-->>C: Dotted line with arrowhead
  B-)C: Solid line with Async arrow
  B--)C: Dotted line with Async arrow
  B-xC: Solid line with a cross at end
  B--xC: Dotted line with a cross at end
  %% activation, shorthand
  activate Alice
  B->>+C: Arrow with + that activates Carol
  C->>-B: Arrow with - that deactivates Carol
  deactivate Alice
  %% notes
  Note left of Alice: Alice likes to chat
  Note over B,C: Bob whispers when sick
  %% loop
  loop Every minute
    B-->C: Can you hear me?
  end
  %% alt
  alt is sick
    B-->C: Not so good :(
  else is well
    B->C: Feeling fresh like a daisy
  end
  opt Extra response
    B->C: You, Carol?
  end
  %% par
  par Action 1
    B-->C: I'm good
  and Action 2
    B->>C: I'm better now
  end
  rect rgba(128, 128, 128, 0.5)
    B->>C: So colourful!
  end
```

``` mermaid
graph TB %% comments
  %% Entity[Text]
  ID-1[Node 1]
  ID-2>Node 2]
  ID-3(Node 3 <br> text)
  %% Entity--Entity
  ID-1---ID-2
  ID-1 --> ID-3
  %% Entity--Text--Entity
  ID-2--Link between 2 and 3---ID-3
  ID-3-->|Action from 3 to 1|ID-1
  ID-3 -- "Action from 3 to 2. p/w: '_-!#$%^&*+=?,\'" --> ID-2
  %% Complex cases
  A[Hard edge] -->|Link text| B(Round edge)
  ID-1---ID-2(Text)
  B --> C{Text}
  C -->|One| D[Text]
  A(A) --> B(B)
  C[/C/] --> D>D]
  %% class/classDef
  classDef blue fill:#08f,stroke:#fff;
  class ID-1 blue
  class ID-1,ID-2 red
  %% click
  click ID-1 "https://github.com" "Tooltip text" %% comments
  click ID-2 alert "Tooltip for a callback"
  %% subgraph
  subgraph A subgraph
    ID-4{Node 4}
    ID-5((fa:fa-spinner))
    ID-6["Node 6 (same #quot;shape#quot;)"]
    ID-4-.->ID-5
    ID-5 -. Action from 5 to 4 .-> ID-4
    ID-5==>ID-6
    ID-6 == Action from 6 to 5 ==> ID-5
  end
```

```mermaid
gantt %%comment
  dateFormat  YYYY-MM-DD
  axisFormat  %m/%d/%Y
  title Adding GANTT diagram functionality to mermaid
  section A section %%comment
  Completed task            :done,    des1, 2014-01-06,2014-01-08
  Active task               :active,  des2, 2014-01-09, 3d
  Future task               :         des3, after des2, 5d %%comment
  Future task2               :         des4, after des3, 5d
  A task           :a1, 2014-01-01, 30d
  section Critical tasks
  Completed task in the critical line :crit, done, 2014-01-06,24h
  Implement parser and jison          :crit, done, after des1, 2d
  Create tests for parser             :crit, active, 3d
  Future task in critical line        :crit, 5d
  Create tests for renderer           :2d
  Add to mermaid                      :1d
```

``` mermaid
  pie
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
```

``` mermaid
classDiagram
  Animal <|-- Duck : LabelText
  class1 --o other
  Animal --o Fish
  Animal : +int age
  Animal : +String gender
  Animal: mate()
  Animal : #method(param)* return
  class Duck{
      %% Class Members
      +String beakColor
      #quack()
  }
  class Fish{
      -abstractMethod()*
      staticMethod()$
  }
  %% Class member generics
  class Square~Shape~{
      List~int~ position
      setPoints(List~int~ points)
      getPoints() List~int~
  }
  Square : -List~string~ messages
  Square : ~setMessages(List~string~ messages)
  Square : +getMessages() List~string~

  %% Multiplicity relations
  Customer "1" --> "*" Ticket
  Student "1" --> "1..*" Course
  Galaxy --> "6" Star : Contains

  %% Annotations
  class Annotate1
  <<interface>> Animal

  class Annotate2{
    <<Service>>
  }
```


``` mermaid
graph TB
    sq[Square shape] --> ci((Circle shape))

    subgraph A
        od>Odd shape]-- Two line<br/>edge comment --> ro
        di{Diamond with <br/> line break} -.-> ro(Rounded<br>square<br>shape)
        di==>ro2(Rounded square shape)
    end

    %% Notice that no text in shape are added here instead that is appended further down
    e --> od3>Really long text with linebreak<br>in an Odd shape]

    %% Comments after double percent signs
    e((Inner / circle<br>and some odd <br>special characters)) --> f(,.?!+-*ز)

    cyr[Cyrillic]-->cyr2((Circle shape Начало));

     classDef green fill:#9f6,stroke:#333,stroke-width:2px;
     classDef orange fill:#f96,stroke:#333,stroke-width:4px;
     class sq,e green
     class di orange
```

``` mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
```