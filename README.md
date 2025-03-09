#include <iostream>
#include <ctime>
#include <string>
#include <windows.h>

using namespace std;
void drawBoard(char *spaces);
void playerMove(char *spaces, char player);
void computerMove(char *spaces, char computer);
bool checkWinner(char *spaces, char player, char computer);
bool checkTie(char *spaces);
int main(){
    system("color f4");
    string anything, username, password, no;
    cout << "++++++++++++++++++++++++++++++" << endl;
    cout << "========GAME STARTED==========" << endl;
    cout << "++++++++++++++++++++++++++++++" << endl;
    do {
    cout << "Enter your Username: ",
    cin >> username;
    cout << "Enter your Password: ";
    cin >> password;
    cout << endl;
    if(username == "boss" && password == "123456"){
    cout << "===========================" << endl;
    cout << "Successfully Logged In Boss" << endl;
    cout << "===========================" << endl;
    break;
    }
    else {
        cout << "=======================" << endl;
        cout << "Invalid Info ka Boss!!!" << endl;
        cout << "=======================" << endl;
    }
    cout <<endl;
}while(true);
cout << endl;
cout << "+++++++++++++++++++++++++++++++++++++++++++++" << endl;
cout << "======WELCOME TO TIC TAC TOE GAME BOSS!======" << endl;
cout << "+++++++++++++++++++++++++++++++++++++++++++++" << endl;
system("pause");
system("color 3");
do{

        char spaces[9] = {' ',' ',' ',' ',' ',' ',' ',' ',' '};
        char player = 'X';
        char computer = '0';
        bool running = true;

        drawBoard(spaces);

        while(running){
            playerMove(spaces, player);
            drawBoard(spaces);
            if(checkWinner(spaces, player, computer)){
                running = false;
                break;
            }

            else if(checkTie(spaces)){
                running = false;
                break;
            }

            computerMove(spaces, computer);
            drawBoard(spaces);
            if(checkWinner(spaces, player, computer)){
                running = false;
                break;
            }

            else if(checkTie(spaces)){
                running = false;
                break;
            }
        }
            cout <<endl;
            cout << "===========================" << endl;
            cout << "Do you want to play again? (yes/no) ";
            cin >> anything;
            cout << endl;

            } while(anything == "yes" || anything == "YES" || anything == "Yes");

            if(no == no){
                cout << "++++++++++++++++++++++++++++++++++++++" << endl;
                cout << "Goodbye Boss! Thank you for playing Boss!!!" << endl;
                cout << "++++++++++++++++++++++++++++++++++++++" << endl;
            }
}

void drawBoard(char *spaces){
        cout << "__________________" << '\n';
        cout << "     |     |     |" << '\n';
        cout << " " << spaces[0] << "   |  "  << spaces[1] << "  |  " << spaces[2] << "  | " << '\n';
        cout << "_____|_____|_____|" << '\n';
        cout << "     |     |     |" << '\n';
        cout << " " << spaces[3] << "   |  "  << spaces[4] << "  |  " << spaces[5] << "  | " << '\n';
        cout << "_____|_____|_____|" << '\n';
        cout << "     |     |     |" << '\n';
        cout << " " << spaces[6] << "   |  "  << spaces[7] << "  |  " << spaces[8] << "  | " << '\n';
        cout << "_____|_____|_____|" << '\n';
        cout << '\n';
    }
void playerMove(char *spaces, char player){
        int number;
        do{
            cout << "Enter a spot to place a marker (1-9) ";
            cin >> number;
            number--;
            if (spaces[number] == ' '){
                spaces[number] =
                player;
                break;
            }
        }while(!number > 0 || !number < 8);
}
void computerMove(char *spaces, char computer){
    int number;
    srand(time(0));

    while(true){
        number = rand() % 9;
        if(spaces[number] == ' ');
        spaces[number] = computer;
        break;
    }
}
bool checkWinner(char *spaces, char player, char computer){
    if((spaces[0] != ' ') && (spaces [0] == spaces[1]) && (spaces[1] == spaces[2])){
                            cout << "===========================" << endl;
        spaces[0] == player ? cout << "You have slain an Enemy\n" : cout << "Loser!!!\n";
    }
     else if((spaces[3] != ' ') && (spaces [3] == spaces[4]) && (spaces[4] == spaces[5])){
                            cout << "===========================" << endl;
        spaces[3] == player ? cout << "You have slain an  Enemy\n" : cout << "Loser!!!\n";
    }
     else if((spaces[0] != ' ') && (spaces [0] == spaces[3]) && (spaces[6] == spaces[6])){
                            cout << "===========================" << endl;
        spaces[0] == player ? cout << "You have slain an  Enemy!!!\n" : cout << "Loser!!!\n";
    }
     else if((spaces[1] != ' ') && (spaces [1] == spaces[4]) && (spaces[7] == spaces[7])){
                            cout << "===========================" << endl;
        spaces[1] == player ? cout << "You have slain an  Enemy\n" : cout << "Loser!!!\n";
    }
    else if((spaces[2] != ' ') && (spaces [2] == spaces[5]) && (spaces[5] == spaces[8])){
                            cout << "===========================" << endl;
        spaces[2] == player ? cout << "You have slain an  Enemy\n" : cout << "Loser!!!\n";
    }
     else if((spaces[0] != ' ') && (spaces [0] == spaces[4]) && (spaces[4] == spaces[8])){
                            cout << "===========================" << endl;
        spaces[0] == player ? cout << "You have slain an  Enemy\n" : cout << "Loser!!!\n";
    }
       else if((spaces[2] != ' ') && (spaces [2] == spaces[4]) && (spaces[4] == spaces[6])){
                            cout << "===========================" << endl;
        spaces[2] == player ? cout << "You have slain an  Enemy!!!\n" : cout << "Loser!!!\n";
    }
      else{
        return false;
      }
    return true;
}
bool checkTie(char *spaces){

    for(int i = 0; i < 9; i++){
        if(spaces[i] == ' '){
            return false;
        }
    }
    cout << "================" << endl;
    cout << "It's a Tie Boss";
    cout << "================" << endl;
    return true;
}




