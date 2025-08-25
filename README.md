# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```python
#include <stdio.h>
#include <string.h>

void railFenceEncrypt(char text[], int key) 
{
    int len = strlen(text);
    char rail[key][len];
    
    for(int i=0;i<key;i++)
        for(int j=0;j<len;j++)
            rail[i][j] = '\n';
    
    int row = 0, dir = 0;
    for(int i=0;i<len;i++) {
        rail[row][i] = text[i];
        if(row==0) dir = 1;
        else if(row==key-1) dir = 0;
        row += dir ? 1 : -1;
    }
    
    printf("Cipher Text: ");
    for(int i=0;i<key;i++)
        for(int j=0;j<len;j++)
            if(rail[i][j] != '\n')
                printf("%c", rail[i][j]);
}

int main() 
{
    char text[100];
    int key;
    
    printf("Enter plain text: ");
    scanf("%s", text);
    printf("Enter key (number of rails): ");
    scanf("%d", &key);
    
    railFenceEncrypt(text, key);
    
    return 0;
}
```
# OUTPUT

<img width="1637" height="906" alt="image" src="https://github.com/user-attachments/assets/e50de88d-b023-457e-aad8-13b710490381" />


# RESULT

Thus The Program Has Been Successfully Initiated
