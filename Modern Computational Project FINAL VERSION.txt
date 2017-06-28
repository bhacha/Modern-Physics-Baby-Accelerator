import time
from random import randint
from datetime import datetime as dt
import datetime
import matplotlib.pyplot as plt
today=dt.today()
#realTime= delta time between the real dates 
#expTime= delta time experienced by babies (new age)
year=2254
Start=True
c= 3 * 10**8
#Speed of Light
#gamma = 1/(1-(v**2/c**2))**(.5)
#v= (((1-(1/gamma))*c**2)**.5)/(3*10**8)
babies=15
#number of babies
baby = {}
#dictionary
age=[]
velocity=[]
#these two lists will be plotted
#option = input('HELLO. WELCOME TO HACHA-TEC INFANT ACCELERATOR. WHAT WOULD YOU LIKE TO DO TODAY? (ENTER THE NUMBER OF YOUR SELECTION)' + '\n' + '1. SYNCHRONIZE BABIES' + '\n' + '2. VIEW PROGRAM DETAILS' + '\n' + '3. CONFIGURE SYSTEM' + '\n'  +'\n')


while Start==True :
#This narrows looping down to invalid menu entries only   
    option = input('\n'+ 'HELLO. WELCOME TO HACHA-TEC INFANT ACCELERATOR. WHAT WOULD YOU LIKE TO DO TODAY? (ENTER THE NUMBER OF YOUR SELECTION)' + '\n' + '1. SYNCHRONIZE BABIES' + '\n' + '2. VIEW PROGRAM DETAILS' + '\n' + '3. CONFIGURE SYSTEM' + '\n'  +'\n')       
    while option > '0' and option < '4': 
        if option == '1':
            print('THANK YOU FOR CHOOSING HACHA-TEC FOR YOUR INFANT ACCELERATING. PLEASE WAIT WHILE PROGRAM LOADS.' + '\n')
            time.sleep(0)
            print( str(babies) + ' INFANTS WILL BE SET FOR ACCELERATION.' + '\n')     
            
            realDate2=input('ENTER DATE ON WHICH TO FINISH SYNCHRONIZING INFANTS IN MM-DD-YYYY FORMAT' + '\n')
            #gives date for infants to finish process
            expTime1=input('WHAT AGE (IN DAYS) DO YOU WANT INFANTS TO BE?' +'\n')
            #gives age for infants to be once they finish
            expTime2=dt.strptime(realDate2,'%m-%d-%Y')
            #the ends of the aging is the same for the "real" and experienced, this gives date
            newBirthday= expTime2 - datetime.timedelta(days=int(expTime1))
            #this just subtracts the age of the baby to give the new birth date
            print('THE NEW BIRTHDAY FOR THESE INFANTS WILL BE ' + str(newBirthday) +'.' +'\n')
            
            manual=input('MAKE SELECTION:' + '\n'+'1. RUN SIMULATION WITH RANDOM STARTING AGES'+ '\n' +'2. MANUALLY INPUT BIRTHDATES'+ '\n' )
            if manual == '1':
                for i in range(0, int(babies)):
                    baby[i]= randint(1,364)
                    gamma= baby[i]/int(expTime1)
                    #converts value from timedelta to days and converts desired age into integer
                    v= (((1-(1/gamma))*c**2)**.5)/(3*10**8)
                    #Calculates the needed velocity
                    age.append(baby[i])
                    velocity.append(v)
                   #Creates list with values
                
                
                plt.scatter(age, velocity)
                plt.xlabel('Starting Age in Days')
                plt.xlim([0,366])
                plt.ylabel('Velocity as Factor of C')
                plt.ylim([0,1.01])
                plt.show()
                
                
                option=input('1. PRESS 4 TO GO BACK' + '\n')
               
            
            
            if manual == '2':
                for i in range (0, int(babies)):
                    realDate1=input('ENTER INFANT'+ str(i+1) +'\'S' + ' CURRENT BIRTHDATE IN MM-DD-YYYY FORMAT' + '\n')
                    baby[i]= realAge= dt.strptime(realDate2, '%m-%d-%Y') -  dt.strptime(realDate1, '%m-%d-%Y')
                    #print(baby[i]) ///for debugging
                    gamma= baby[i].days/int(expTime1)
                    #converts value from timedelta to days and converts desired age into integer
                    v= (((1-(1/gamma))*c**2)**.5)/(3*10**8)
                    age.append(baby[i].days)
                    velocity.append(v)
                
                
                plt.scatter(age, velocity)
                plt.show()
                plt.xlabel('Age in Days')
                plt.xlim([0,366])
                plt.ylabel('Velocity as Factor of C')
                plt.ylim([0,1.01])
            
                
                option=input('1. PRESS 4 TO GO BACK' + '\n')
            #Pressing 4 changes option to 4 and brings back to the option input
            
        while option == '2':
            print('\n'+'HACHA-TEC\'S INFANT ACCELERATOR WAS CREATED TO SOLVE THE PROBLEM OF AGE INEQUALITY IN SCHOOL GRADE LEVEL POPULATIONS.'+'\n' + 'FOR MUCH TOO LONG, CHILDREN BORN AT THE END OF THE SCHOOL YEAR HAVE BEEN FORCED TO BE EITHER MUCH YOUNGER OR MUCH OLDER THAN THEIR PEERS. THE INFANT ACCELERATOR SOLVES THIS PROBLEM RELATIVISTICALLY.' +'\n' + 'ONCE THE CHILD\'S BIRTHDAY IS DETERMINED, THE CHILD IS ACCELERATED TO A CERTAIN VELOCITY AND THEREFORE BECOMES ASSIGNED A NEW BIRTHDAY.' )
            #This just provides details
            option=input('PRESS 4 TO GO BACK')
            
        while option == '3':
            #This opens config menu to change the pre-set variables
                config=input('\n'+'WHAT WOULD YOU LIKE TO CONFIGURE? (ENTER THE NUMBER OF YOUR SELECTION)' + '\n' + '1. YEAR' +'\n' + '2. CHANGE NUMBER OF INFANTS' +'\n' + '3. GO BACK' +'\n')   
               #Can be updated with other variable prompts
        #        while (config!= '1'):
        #           config=input('WHAT WOULD YOU LIKE TO CONFIGURE? (ENTER THE NUMBER OF YOUR SELECTION)' + '\n' + '1. YEAR' +'\n' + '2. GO BACK' +'\n')   
               #loops if invalid menu choice made
                if config == '1':
                    year = input('WHAT IS THE CURRENT YEAR?:   ')
                    leap = int(year) % 4
                    #Leap years are evenly divisible by 4. Some exceptions, but none we'll see.
                    if (leap > 0 ):
                        print('\n'+'THIS IS NOT A LEAP YEAR. CHANGES SAVED')
                        global option
                        option='4'
                        #This redefines the option variable and brings the user back to the main menu
                        
                    else:
                        print('\n'+'THIS IS A LEAP YEAR. CHANGES SAVED.')
                        global option
                        option='4'
                        # This also redefines the variable and brings the user back
                        
                elif config == '2':
                    global babies
                    babies=input('HOW MANY INFANTS WILL BE ADJUSTED?' + '\n')
                    print('CHANGES SAVED. ADJUSTING '+ babies + ' INFANTS.')
                    global option
                    option = '4'
                    #Changes the number of babies in unit and then brings user back
                else:
                    global option
                    option='4'
                    #print(option) //Used for debug
                    continue
                    #Brings user back to main menu
                    
                    
    
