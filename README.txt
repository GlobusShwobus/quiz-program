#include <iostream>
#include <stdlib.h>
using std::cout;
using std::endl;
using std::string;
using std::cin;

class QuizGame {                                //making the quiz into a class to glue it all together
public:
    struct Quiz {
        string question[5];
        string answer[3];
        int correct[5];
    };
    QuizGame() {                         //initializer
        Quiz block[5];                   //idk why i named it block, because blocks of text probably
        AnswerSheet(block);
        QuizScript(block);
    }
    void QuizScript(Quiz block[5]) {    //this was truly cursed for me, i deleted probably 1.5k lines of code starting over and over again
        int option = 0;                 // at points this function really was cursed, made the program hard crash
                                        //works now :d
        for (int i = 0; i < 5; i++) {
            for (int j = 0; j < 5; j++) {              //this was left over from iterating many times, I'm not sure this is needed
                cout << block[0 + i].question[0 + i] << endl;
                cout << block[0 + i].answer[0] << endl;
                cout << block[0 + i].answer[1] << endl;
                cout << block[0 + i].answer[2] << endl;
                block[0].correct[0 + i];
                cout << "Select 1-3: ";
                while (!(cin >> option)) {                    //if input is anything else than an int 
                    cout << endl << "ERROR: invalid option:\nSelect 1-3: ";
                    cin.clear();
                    cin.ignore(123, '\n');
                }
                if (option == block[0].correct[0 + i]) {
                    cout << endl << "**Correct**" << endl << endl;
                    break;                     //no break = unintended behavior
                }
                else if (option != block[0].correct[0 + i]) {//???
                    cout << endl << "**IN_Correct**" << endl << endl;
                    break;                    //no break = unintended behavior
                }
            }
            EXIT_SUCCESS;                  //just in case because from previous iterations the program hard crashed
        }
    }
    void AnswerSheet(Quiz block[5]) {
        block[0].question[0] = "**Most popular programming language?**";
        block[0].answer[0] = "1.Java";
        block[0].answer[1] = "2.Python";
        block[0].answer[2] = "3.C++";
        block[1].question[1] = "**Which of these does not belong?**";
        block[1].answer[0] = "1.World of Warcraft";
        block[1].answer[1] = "2.Elder scrolls online";
        block[1].answer[2] = "3.Call of duty";
        block[2].question[2] = "**Most sold game ever?**";
        block[2].answer[0] = "1.Minecraft";
        block[2].answer[1] = "2.GTA5";
        block[2].answer[2] = "3.Tetris";
        block[3].question[3] = "**Worlds biggest industry?**";
        block[3].answer[0] = "1.Automobil";
        block[3].answer[1] = "2.Fossil fuel";
        block[3].answer[2] = "3.Tech";
        block[4].question[4] = "**Game of the decade contendor?**";
        block[4].answer[0] = "1.Genshin Impact";
        block[4].answer[1] = "2.Elden ring";
        block[4].answer[2] = "3.Starfield";

        block[0].correct[0] = 1;
        block[0].correct[1] = 3;
        block[0].correct[2] = 1;
        block[0].correct[3] = 3;
        block[0].correct[4] = 2;
    }
};

int main()
{
    QuizGame player1;

    return 0;
}

/*
A short C++ quiz program. Made it after watching the codeBeauty structures guide.
This is not my first code but it is the first one that took effort, even though it's only 80 lines.
I'm new to coding. This was done after 2 months from starting from 0.
I would love it if people just took a glance and left suggestions where I could improve or a general direction
I should head. At the moment I am keen on focusing on C++, but maybe in a year I could branch out to Java
for web stuff.
*/
