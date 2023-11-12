#include <iostream>
#include <string>
#include <fstream>
#define LINE_COUNTER 21

using std::cout;
using std::endl;
using std::string;
using std::cin;

class QuizGame {                  
public:
    struct Quiz {
        string question[5];
        string answer[3];
        int correct[5] = { 1,3,1,3,2 };
        int points = 0;
    }rewards;

    QuizGame() {
        Quiz block;                
        QuizScript(block);
        system("pause");
        RewardShop();
    }
    void QuizScript(Quiz block) {
        int option = 0;
        int lines = 0;
        string print[LINE_COUNTER];
        
        std::fstream Text("Quiz_QnA");
        Text.open("Quiz_QnA.txt");
        while (!Text.eof()) {
            std::getline(Text, print[lines]);
            lines++;
        }
        Text.close();

        int num[5][4] = { {0,1,2,3},{4,5,6,7},{8,9,10,11},{12,13,14,15},{16,17,18,19} };//hardcoded line coordinates
        
        for (int i = 0; i < 5; i++) {
            for (int j = 0; j < 4; j++) {
                cout << print[num[i][j]] << endl;
            }
            for (int k = 0; k < 5; k++) {
                cout << "Select 1-3: ";
                while (!(cin >> option)) {
                    cout << endl << "ERROR: invalid option:\nSelect 1-3: ";
                    cin.clear();
                    cin.ignore(123, '\n');
                }
                if (option == block.correct[i]) {
                    cout << endl << "**Correct**" << endl << endl;
                    rewards.points++;
                    break;
                }
                else if (option != block.correct[i]) {
                    cout << endl << "**IN_Correct**" << endl << endl;
                    break;
                }
            }
        }
        cout << "You earned >> " << rewards.points << " << points" << endl << endl;
    }
    void RewardShop() {
        int reward;
        int value[5] = { 1,2,3,4,5 };

        system("cls");
        while (rewards.points > 0) {//thought no point in adding thsi to .txt becasue it would add needless complexity, but idk lol
            cout << "***PICK A PRIZE***" << endl;
            cout << "You have: " << rewards.points << " Points" << endl << endl;
            cout << "1. Snikers- 1 Point" << endl;
            cout << "2. Instant Coffee- 2 Points" << endl;
            cout << "3. $20 IKEA giftcard- 3 Points" << endl;
            cout << "4. 40 MB floppyd disc- 4 Points" << endl;
            cout << "5. Extra long snikers- 5 Points" << endl;
            cout << "Select: ";
            while (!(cin >> reward)) {
                cout << endl << "ERROR: invalid option:\nSelect: ";
                cin.clear();
                cin.ignore(123, '\n');
            }
            switch (reward) {
            case 1: if (rewards.points < value[0]) {
                cout << endl << "Insufficient funds" << endl << endl; break;
            }
                  else {
                rewards.points -= value[0];
                cout << "Enjoy: Snikers" << endl;
                cout << "~~~~~~~~~~" << endl << endl;  break;
            }
            case 2: if (rewards.points < value[1]) {
                cout << endl<< "Insufficient funds" << endl << endl; break;
            }
                  else {
                rewards.points -= value[1];
                cout << "Enjoy: Coffee" << endl;
                cout << "~~~~~~~~~~" << endl << endl;  break;
            }
            case 3: if (rewards.points < value[2]) {
                cout << endl << "Insufficient funds" << endl << endl; break;
            }
                  else {
                rewards.points -= value[2];
                cout << "Enjoy: Big Value" << endl;
                cout << "~~~~~~~~~~" << endl << endl;  break;
            }
            case 4: if (rewards.points < value[3]) {
                cout << endl << "Insufficient funds" << endl << endl; break;
            }
                  else {
                rewards.points -= value[3];
                cout << "Enjoy: Nostalgia" << endl;
                cout << "~~~~~~~~~~" << endl << endl;  break;
            }
            case 5: if (rewards.points < value[4]) {
                cout << endl << "Insufficient funds" << endl << endl; break;
            }
                  else {
                rewards.points -= value[4];
                cout << "Enjoy: scam" << endl;
                cout << "~~~~~~~~~~" << endl << endl;  break;
            }
            default: cout<< endl << "Insufficient funds" << endl << endl; break; EXIT_SUCCESS;
            }      
        }
        EXIT_SUCCESS; 
    }
};

int main()
{
    QuizGame player1;

    return 0;
}