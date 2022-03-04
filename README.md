#include <stdio.h>
#include <stdlib.h>


void sub(int * num1, int index1, int * num2, int index2, int head1, int head2);


int main() {
	
	char charNum1[300] = {'\0'};
	char charNum2[300] = {'\0'};
	scanf("%s", charNum1);
	scanf("%s", charNum2);

	int index1 = 0;
	int index2 = 0;
	while(charNum1[index1] != '\0')
		index1++;
	while(charNum2[index2] != '\0')
		index2++;
		

	
	int num1[300] = {-1};
	int num2[300] = {-1};

	for(int i = 0; i < index1; i++)
	{
		char num[2] = {charNum1[i], '\0'};
		int temp = atoi(num);
		num1[i] = temp;
	}
	for(int i = 0; i < index2; i++)
	{
		char numc[2] = {charNum2[i], '\0'};
		int temp2 = atoi(numc);
		num2[i] = temp2;
	}
	
	int * ptr_num1 = num1;
	int * ptr_num2 = num2;
    int head1 = 0;
    int head2 = 0;
    int tail1 = index1 - 1;
    int tail2 = index2 - 1;
	printf("%d \n", head2);
	
	
	while(1)
	{
	    int flag = 0;
	    int len1 = tail1 - head1 + 1;
	    int len2 = tail2 - head2 + 1;
	    //printf("%d\n", tail1);
	    //if(len1 == 1 && (*(ptr_num1 + tail1) == 0))
	    //    break;
	    //else
	    //{
	        //printf("yes\n");
	        //printf("%d %d\n", len1, len2);
	        
            if(len2 > len1)
        	{
        	    //printf("yes\n");
        		int temp = index1;
        		index1 = index2;
        		index2 = temp;
        		
        		int temp3 = head1;
        		head1 = head2;
        		head2 = temp3;
         		
        		int * temp2 = ptr_num2;
        	    ptr_num2 = ptr_num1;
        	    ptr_num1 = temp2;
        	}
        	else if(len1 == len2)
        	{
        	    int temph2 = head2;
        	    
        	    //printf("%d\n", tempHead2);
        	    for(int i = head1; i < index1; i++)
        		{
        			if(num2[temph2] > num1[i])
        			{
        				printf("yes\n");
        				int temp = index1;
        				index1 = index2;
        				index2 = temp;
        				
        				int temp3 = head1;
        		        head1 = head2;
        		        head2 = temp3;
        				
        				int * temp2 = ptr_num2;
        	            ptr_num2 = ptr_num1;
        	            ptr_num1 = temp2;
        	            flag = 1;
        				break;
        			}
        			temph2 += 1;
        		}
        		
        	} 
	   // }
	    
	    if(flag == 0)
	        break;
	        
	    sub(ptr_num1, index1, ptr_num2, index2, head1, head2);
	    
	    for(int i = 0; i < index1; i++)
	    {
	        if(*(ptr_num1 + i) > 0)
	        {
	            head1 = i;
	            break;
	        }
	            
	    }
	    for(int i = 0; i < index2; i++)
	    {
	        if(*(ptr_num2 + i) > 0)
	        {
	            head2 = i;
	            break;
	        }
	            
	    }
	    
	}
	

    

	
	
	
	for(int i = head1; i < index1; i++)
	{
		printf("%d", *(ptr_num1 + i));
	}
	
	printf("\n");
	
	for(int i = head2; i < index2; i++)
	{
		printf("%d", *(ptr_num2 + i));
	}
	
	//free(ptr_index1);
	//free(ptr_num1);
	//free(ptr_index2);
	//free(ptr_num2);
	
	return 0;
}



void sub(int * num1, int index1, int * num2, int index2, int head1, int head2)
{
	int tempindex;
	int c2 = index2;
	for(int i = index1; i >= head1; i--)
	{
		if(c2 < head2)
			break;
		
		if(num1[i] < num2[c2])
		{
			tempindex = i;
			while(1)
			{
				if(num1[tempindex-1]>0)
				{
					num1[i] += 10;
					num1[tempindex-1]--;
					break;
				}
				else
					tempindex--;
			}
		}
		
		num1[i] -= num2[c2];
		c2--;
	}
}




