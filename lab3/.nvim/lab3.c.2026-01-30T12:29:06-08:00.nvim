#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

int main(void) {

  char *line = NULL;
  size_t size = 0;
  size_t read;

  // pointer array to store strings
  char *buffer[5] = {0};
  int count = 0;

  while (1) {
    printf("Enter input: ");
    read = getline(&line, &size, stdin);

    if (read == -1) {
      break;
    }

    if (line[read - 1] == '\n') {
      line[read - 1] = '\0';
    }

    // 5 strings only manager
    if (count == 5) {
      free(buffer[0]); // delete last entry
      for (int i = 1; i < 5; i++) {
        // shift down all entries in array
        buffer[i - 1] = buffer[i];
      }
      count--;
    }

    // put line into pointer array
    buffer[count] = strdup(line);
    count++;

    if (strcmp(line, "print") == 0) {
      for (int i = 0; i < count; i++) {
        printf("%s\n", buffer[i]);
        free(buffer[i]);
      }
      count = 0;
    }
  }

  for (int i = 0; i < count; i++) {
    free(buffer[i]);
  }

  return 0;
}
