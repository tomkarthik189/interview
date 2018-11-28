#include <stdio.h> 
#include <string.h> 
#include <stdlib.h> 
  

char *replaceWord(const char *s, const char *oldW, 
                                 const char *newW) 
{ 
    char *result; 
    int i, cnt = 0; 
    int newWlen = strlen(newW); 
    int oldWlen = strlen(oldW); 
  
    
    for (i = 0; s[i] != '\0'; i++) 
    { 
        if (strstr(&s[i], oldW) == &s[i]) 
        { 
            cnt++; 
  
             
            i += oldWlen - 1; 
        } 
    } 
  
     
    result = (char *)malloc(i + cnt * (newWlen - oldWlen) + 1); 
  
    i = 0; 
    while (*s) 
    { 
        // compare the substring with the result 
        if (strstr(s, oldW) == s) 
        { 
            strcpy(&result[i], newW); 
            i += newWlen; 
            s += oldWlen; 
        } 
        else
            result[i++] = *s++; 
    } 
  
    result[i] = '\0'; 
    return result; 
} 
  

int main() 
{ 
    char str[] = "mô5t "; 
    char c[] = "xx"; 
    char d[] = "một"; 
  
    char *result = NULL; 
  
    
    printf("Old string: %sn", str); 
  
    result = replaceWord(str, c, d); 
    printf("New String: %sn", result); 
  
    free(result); 
    return 0; 
} 
