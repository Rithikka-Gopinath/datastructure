#include <stdio.h>
#include <stdlib.h>

char* longestCommonPrefix(char** strs, int strsSize) {
    int i = 0;
    int j = 0;
    int k = 0;
    char* w = malloc(sizeof(char) * 200); // Allocating space for the result
    if (w == NULL) return NULL; // Check for memory allocation failure
    w[0] = '\0'; // Initialize the result string

    char* ptr = strs[0]; // Reference to the first string
    while (ptr[j] != '\0') { // Iterate through characters of the first string
        for (i = 1; i < strsSize; i++) {
            if (strs[i][j] != ptr[j]) { // Check for mismatch
                w[k] = '\0'; // Null terminate the string
                return w; // Return the common prefix found so far
            }
        }
        w[k++] = ptr[j]; // Add the matching character to the result
        j++; // Move to the next character
    }

    w[k] = '\0'; // Null terminate the final result
    return w; // Return the common prefix
}
