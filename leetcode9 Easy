

bool isPalindrome(int x){
    int rem,temp,sum=0;
    temp=x;
    while(x!=0){
        rem=x%10;
        if(sum>INT_MAX/10 || sum<INT_MIN/10)
            return false;
    sum=(sum*10)+rem;
    x=x/10;
    }
    if(sum<0)
        sum=-sum;
    if(sum==temp){
        return true;
    }
    else if(sum==-temp)
        return false;
    else
      return  false;
    }
