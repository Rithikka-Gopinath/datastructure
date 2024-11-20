#include <stdlib.h>
#include <string.h>

int findSymbol(char c, char *symbolArr)
{
    int j = 0;
    while(c != symbolArr[j])
        j++;
    return (j);
}

int romanToInt(char* s) 
{
    int symbolIndex;
    int nextSymbolIndex;
    int i = 0;
    int finalNum = 0;
    int strLen = strlen(s);

    char symbolArr[] = {'I', 'V', 'X', 'L', 'C', 'D', 'M'};
    int valueArr[] = {1, 5, 10, 50, 100, 500, 1000};

    while (s[i] && i < (strLen - 1))
    {
        symbolIndex = findSymbol(s[i], symbolArr);
        nextSymbolIndex = findSymbol(s[i + 1], symbolArr);
        if (symbolIndex < nextSymbolIndex)
        {
            finalNum += (valueArr[nextSymbolIndex] - valueArr[symbolIndex]);
            i += 1;
        }
        else
            finalNum += valueArr[symbolIndex];
        i++;
    }
    if (s[i] && i < strLen)
    {
        symbolIndex = findSymbol(s[i], symbolArr);
        finalNum += valueArr[symbolIndex];
    }
    return (finalNum);
}
