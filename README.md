# jms
#include <stdio.h>
#include <math.h>

int main() {

    int noOfUserStory, i, storyPoint[25], velocity, workingDaysInWeek, iterationLength, sum=0, ref=-1;
    int iteration=0, k, j=0, workingDays=0, holidays=0, totalDays=0;
    float arr[3], userStory[25];

    clrscr();

    //Read no.of user story
    printf("\nNo.of user story : ");
    scanf("%d", &noOfUserStory);
    
    //Read user story name
    printf("\nEnter user story\n");
    for(i=1; i<=noOfUserStory; i++)
        scanf("%f", &userStory[i]);
        
        
    //read story point for each user story
    for(i=1; i<=noOfUserStory; i++) {
        printf("\nStory point for %1.1f : ", userStory[i]);
        scanf("%d", &storyPoint[i]);
    }
    
    //read team velocity
    printf("\nEnter team velocity : ");
    scanf("%d", &velocity);
    
    //read working days in week
    printf("\nNo.of working days in week : ");
    scanf("%d", &workingDaysInWeek);

    //read iteration length
    printf("\nIteration length (weeks) : ");
    scanf("%d", &iterationLength);
    
    
    printf("\n\n\t\tRELEASE PLAN\n");
    printf("--------------------------------------------------------------------------");
    printf("\nIteration\tUser story\tStory point value\n");
    printf("--------------------------------------------------------------------------");
    
    //calculate release plan
    for(i=1; i<=noOfUserStory; i++) {

	if(sum < velocity) {

	    sum += storyPoint[i];
	    arr[++j] = userStory[i];
	}


	if(sum == (velocity+1) || sum == (velocity+2)) {

	    if(ref == 0 || ref == -1 || sum-storyPoint[i] <= velocity-3) {

		ref = 1;
		goto l1;

	    } else {

		sum -= storyPoint[i];
		i -= 1;
		ref = 0;
		j-=1;
		goto l1;
	    }

	}

	if(sum == (velocity-1) || sum == (velocity-2)) {

	    if(sum+storyPoint[i+1] == (velocity+1) || sum+storyPoint[i+1] == (velocity+2) ) {
		if(ref == -1 || ref == 0) {

		    ref = 1;
		    sum += storyPoint[++i];
		    arr[++j] = userStory[i];
		    goto l1;

		} else  {

			ref = 0;
			goto l1;
		}

	    } else if(sum+storyPoint[i+1] == velocity) {

		sum += storyPoint[++i];
		arr[++j] = userStory[++i];
		ref = 0;
	    }

	    else
		ref = 0;
	    goto l1;

	}


	if(sum == velocity) {

	    l1:
		printf("\n\t%d", ++iteration);
		for(k=1; k<=j; k++)
		    printf("\t%1.1f  ", arr[k]);
		printf("\%10d\n", sum);
		sum = 0;
                j=0;
        }
    }
    
    printf("\nNo.of iteration : %d", iteration);
    workingDays = iteration * (iterationLength*workingDaysInWeek);
    printf("\nNo.of working days : %d", workingDays);
    holidays = iteration * ( (7*iterationLength) - (iterationLength*workingDaysInWeek));
    printf("\nNo.of holidays : %d",  holidays);
    totalDays = workingDays + holidays;
    printf("\nThe project will be released in %d days", totalDays);
    printf("\nThe project will be released in approximately %d months", (int)ceil ((float)(totalDays) / (float)30));
    getch();
    return 0;
}
