# Mini-Voting-System
#include <stdio.h>
#include <string.h>

#define MAX_CANDIDATES 5

typedef struct
{
    char name[50];
    int votes;
} Candidate;

void displayCandidates(Candidate candidates[], int count)
{
    printf("\nCandidates:\n");
    for (int i = 0; i < count; i++)
    {
        printf("%d. %s\n", i + 1, candidates[i].name);
    }
}

void castVote(Candidate candidates[], int count)
{
    int choice;
    printf("\nEnter the candidate number you want to vote for (1-%d): ", count);
    scanf("%d", &choice);
    
    if (choice >= 1 && choice <= count)
    {
        candidates[choice - 1].votes++;
        printf("Vote casted for %s.\n", candidates[choice - 1].name);
    } 
    else
    {
        printf("Invalid choice. Please try again.\n");
    }
}

void displayResults(Candidate candidates[], int count)
{
    printf("\nVoting Results:\n");
    for (int i = 0; i < count; i++)
    {
        printf("%s: %d votes\n", candidates[i].name, candidates[i].votes);
    }
}

int main()
{
    Candidate candidates[MAX_CANDIDATES] = 
    {
        {"Alice", 0},
        {"Bob", 0},
        {"Charlie", 0},
        {"David", 0},
        {"Eve", 0}
    };
    
    int choice;
    int numCandidates = 5;

    do
    {
        printf("\nVoting System Menu:\n");
        printf("1. Display Candidates\n");
        printf("2. Cast Vote\n");
        printf("3. Display Results\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice)
        {
            case 1:
                displayCandidates(candidates, numCandidates);
                break;
            case 2:
                castVote(candidates, numCandidates);
                break;
            case 3:
                displayResults(candidates, numCandidates);
                break;
            case 4:
                printf("Exiting the voting system.\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } 
    while (choice != 4);

    return 0;
}
