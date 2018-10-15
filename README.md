// Skynet HK-Aerial
//Nicholas Buckley 10.14.2018

//including everything need for program to run
//cstdlib and ctime are used for random number generator
#include "pch.h"
#include <iostream>
#include <string>
#include <cstdlib>
#include <ctime>

using namespace std;
using std::cout;
using std::cin;
using std::endl;
using std::string;

//Creation of main function
int main()
{
	srand(static_cast<unsigned int>(time(0)));//seed random number generator
	int target, targetLocationPrediction, searchGridHighNumber, searchGridLowNumber, ping; //all ints need for program


	searchGridHighNumber = 64; // starting grid max at 64
	searchGridLowNumber = 1; //starting grid min at 1
	ping = 1; //this is the amount of tries that it will take
	targetLocationPrediction = ((searchGridHighNumber - searchGridLowNumber) / 2) + searchGridLowNumber; //the target location prediction that is used to predict between the min an max
	target = 53; // random number between 1 and 64

	//Introduction text
	cout << "Welcome to Skynet HK-Aerial Target Locator\n\n";
	cout << "Generate Random enemy location on 8x8 grid...\n";
	cout << "The enemy is located at location #" << target << " on 8x8 grid with 1-64 sectors.\n";
	cout << "Skynet HK-Aerial Initializing software....\n";
	//Starting a do loop for the program
	do
	{
		cout << "====================================================================================================================\n";//spacing
		cout << "Skynet HK-Aerial Radar sending out ping #" << ping << "\n"; //printing number of tries

		++ping;//increasing number of tries by 1 each time
		targetLocationPrediction = ((searchGridHighNumber - searchGridLowNumber) / 2) + searchGridLowNumber; //changning the prediction each loop based off of max and min of grid

		if (targetLocationPrediction > target)//if the prediction is higher than the target location
		{
			cout << "The taget location prediction of " << targetLocationPrediction << " was ...\n";
			cout << "higher than the actual enemy location of " << target << ".\n";
			searchGridHighNumber = (targetLocationPrediction - 1);//changing the grid max based off of target location
			cout << "The new searchGridHighNumber = " << searchGridHighNumber << ".\n"; //stating the new grid max

		}
		else if (targetLocationPrediction < target)//if the prediction is lower than the target location
		{
			cout << "The taget location prediction of " << targetLocationPrediction << " was ...\n";
			cout << "lower than the actual enemy location of " << target << ".\n";
			searchGridLowNumber = (targetLocationPrediction + 1);//changing the grid man based off of target location
			cout << "The new searchGridLowNumber = " << searchGridLowNumber << ".\n";//stating the new grid min

		}
		else //printed when the target location and prediction equal 
		{
			cout << "Enemy was hiding at location #" << target << ".\n";//stating where the target was
			cout << "Target was found at location #" << target << ".\n";//stating where the traget was found
			cout << "Skynet HK-Aerial Software took " << ping << " predictions to find the enemy location on a grid side of 8x8 (64).\n";//Stating how many tries it took
			cout << "====================================================================================================================\n";
		}
	} while (target != targetLocationPrediction);//Ending the loop once the target and prediction are equal

	return 0;//returning zero to assure no problems



}
