/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int *nums, int numsSize, int target, int *returnSize) 
{
    int *temp = malloc(2 *sizeof(int));
    temp[0] = 0;
    temp[1] = 1;
    for(int i = 0;i < numsSize ;i++)
    {
        for(int j = i + 1; j < numsSize; j++)
        {
            if(nums[i] + nums[j] == target)
            {
                *returnSize = 2;
                temp[0] = i;
                temp[1] = j;
                return temp;

            }
        }
    }
    *returnSize = 0;
    return 0;

    free(temp);
}
