``` mermaid
stateDiagram %%comment
  s1
  state "Description with parenthesis" as s2
  s3 : Description with colon

  s1 --> s2
  s2 --> s3: Colon transition
  [*] --> s1 : Transition text
  s3 --> [*]

```


``` mermaid
stateDiagram %%comment

  state NestedComposite {
      [*] --> Nested

      state Nested {
          [*] --> second
      }
  }

```



``` mermaid
stateDiagram %%comment


  note right of State1
    Important information! You can write
    notes.
  end note
  note left of State2 : This is the note to the left.

  %% concurrency
  state Active {
      [*] --> A
      A --> B : Make payment .

  }
  state InActive {
      B --> NumLockOff
      NumLockOff --> NumLockOn : EvNumLockPressed
      NumLockOn --> NumLockOff : EvNumLockPressed
      --
      [*] --> CapsLockOff
      CapsLockOff --> CapsLockOn : EvCapsLockPressed
      CapsLockOn --> CapsLockOff : EvCapsLockPressed
  }  
```


``` mermaid
stateDiagram %%comment



  %% concurrency
  state Active {
      [*] --> A
      A --> B : Make payment .

  }

```