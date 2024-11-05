//Halimatou Diaby
//Lab 7 




#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>

using namespace std;

// Function to determine the performance message based on the average score
string getPerformanceMessage(double average) {
    if (average > 2000) {
        return "Congrats! You are an Expert!";
    } else if (average >= 1800 && average <= 2000) {
        return "Master - Good Job!";
    } else if (average >= 1500 && average < 1800) {
        return "Advanced - Good Job!";
    } else if (average >= 1000 && average < 1500) {
        return "Intermediate";
    } else {
        return "Beginner - Keep Practicing!";
    }
}

int main() {
    ifstream inputFile("game_scores.txt");

    // Check if the file opened successfully
    if (!inputFile) {
        cerr << "Error: Unable to open file 'game_scores.txt'" << endl;
        return 1;
    }

    string playerName;
    double averageScore;

    // Process each line in the file
    while (inputFile >> playerName >> averageScore) {
        // Calculate individual scores based on the average score
        double score1 = averageScore * 0.20;
        double score2 = averageScore * 0.30;
        double score3 = averageScore * 0.50;

        // Get the performance message for the player
        string message = getPerformanceMessage(averageScore);

        // Output the results for the player
        cout << "Player: " << playerName << endl;
        cout << fixed << setprecision(2);  // Set decimal precision to 2
        cout << "Scores: " << score1 << ", " << score2 << ", " << score3 << endl;
        cout << "Average Score: " << averageScore << endl;
        cout << "Performance: " << message << "\n" << endl;
    }

    inputFile.close();
    return 0;
}
