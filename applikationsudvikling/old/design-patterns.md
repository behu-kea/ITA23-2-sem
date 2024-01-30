# Design Patterns

**Factory Pattern**

Simple example: https://www.tutorialspoint.com/design_pattern/factory_pattern.htm

We are building a simple note-taking application. Initially we have two types of notes (like two different shapes in the above example):

- DraftNote FinishedNote
- All notes consists of:
  - Title from a TextEdit
  - Text from a TextEdit
- Write the application such that:
  - When a user clicks either *save* or *save as draft*
  - A NoteFactory will create either a DraftNote or FinishedNote object
    - Furthermore - the NoteFactory will inform the user by a Toast if a DraftNote or FinishedNote object has been created
- (Advanced) A finished note will furthermore have another attribute: dateFinished
  - The dateFinished attribute contains data when the note was finished - this could be repreesnted by a LocalDate: https://www.baeldung.com/java-8-date-time-intro