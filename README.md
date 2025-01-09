#include <stdio.h>
#include <string.h>
#define n 100
//This c program requires you to input information about employees//
//in a company established in 2001 It then sorts them in descending //
// order based on years of experience and displays the employees who have more than ten years of experience//
struct founctioners{
    char name[30],nickname[30],pin[8];
    int beggin_year;
};
int main(){
    struct founctioners f[n];
    int i,z,found;
    char c[30];

    for(i=0;i<n;i++){
        printf("enter fonctioner %d name : ",i+1);
        scanf("%s",f[i].name);
        printf("enter fonctioner %d nickname : ",i+1);
        scanf("%s",f[i].nickname);
        do{
            found = 0;
            printf("enter fonctioner %d pin : ",i+1);
            scanf("%s",&f[i].pin);
            for(z=0;z<i;z++){
                if(strcmp(f[i].pin, f[z].pin) == 0){
                    found ++;
                }
            }
            if(found != 0){
                printf("\033[31m\ntaht pin already exist\n");
                printf("\033[0m");
            }
        }while(found != 0);
        do{
            printf("enter fonctioner %d beggin year : ",i+1);
            scanf("%d",&f[i].beggin_year);
            if(f[i].beggin_year < 2000){
                printf("\033[31m\neven the company founded in 2000\n");
                printf("\033[0m");
            }
        }while(f[i].beggin_year < 2000);
    }
    for(i=0;i<n;i++){
        for(z=i;z<n;z++){
            if(f[i].beggin_year > f[z].beggin_year){
                strcpy(c ,f[i].name);
                strcpy(f[i].name ,f[z].name);
                strcpy(f[z].name ,c);
                strcpy(c ,f[i].nickname);
                strcpy(f[i].nickname ,f[z].nickname);
                strcpy(f[z].nickname ,c);
            }
        }
    }
    printf("\n\n");
    for(i=0;i<n;i++){
        if(2025 - f[i].beggin_year >= 10){
            printf("the fonctioner %d named %s %s started require in %d\n",i+1,f[i].name,f[i].nickname,f[i].beggin_year);
        }
    }

}
