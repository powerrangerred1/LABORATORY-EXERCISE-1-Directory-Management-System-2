#include <iostream>
#include <direct.h>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;


void list_files() {
    system("dir"); 
}


void list_files_by_extension() {
    string extension;
    cout << "Enter the file extension (e.g., .txt): ";
    cin >> extension;

    string command = "dir *";
    command += extension;
    system(command.c_str()); 
}


void list_files_by_pattern() {
    string pattern;
    cout << "Enter the file pattern (e.g., moha*.*): ";
    cin >> pattern;

    string command = "dir ";
    command += pattern;
    system(command.c_str()); 
}


void create_directory() {
    string dir_name;
    cout << "Enter the name of the directory: ";
    cin >> dir_name;

    if (_mkdir(dir_name.c_str()) == 0) {
        cout << "Directory created successfully." << endl;
    } else {
        cout << "Error creating directory." << endl;
    }
}


void change_directory() {
    int choice;
    cout << "1. Move one step back (to the parent directory)" << endl;
    cout << "2. Move to the root directory" << endl;
    cout << "3. Move to a specific directory" << endl;
    cout << "Enter your choice: ";
    cin >> choice;

    switch (choice) {
        case 1:
            system("cd .."); 
            break;
        case 2:
            system("cd \\"); 
            break;
        case 3: {
            string dir_name;
            cout << "Enter the name of the directory: ";
            cin >> dir_name;

            if (_chdir(dir_name.c_str()) == 0) {
                cout << "Directory changed successfully." << endl;
            } else {
                cout << "Error changing directory." << endl;
            }
            break;
        }
        default:
            cout << "Invalid choice." << endl;
    }
}

int main() {
    while (true) {
        cout << "Main Menu" << endl;
        cout << "1. List files in the current directory" << endl;
        cout << "2. Create a new directory" << endl;
        cout << "3. Change the working directory" << endl;
        cout << "4. Exit" << endl;
        cout << "Enter your choice: ";

        int choice;
        cin >> choice;

        switch (choice) {
            case 1: {
                cout << "List Files Menu" << endl;
                cout << "1. List all files in the current directory" << endl;
                cout << "2. List files based on a specific extension" << endl;
                cout << "3. List files based on a pattern" << endl;
                cout << "Enter your choice: ";

                int file_choice;
                cin >> file_choice;

                switch (file_choice) {
                    case 1:
                        list_files();
                        break;
                    case 2:
                        list_files_by_extension();
                        break;
                    case 3:
                        list_files_by_pattern();
                        break;
                    default:
                        cout << "Invalid choice." << endl;
                }
                break;
            }
            case 2:
                create_directory();
                break;
            case 3:
                change_directory();
                break;
            case 4:
                cout << "Exiting program. Goodbye!" << endl;
                return 0;
            default:
                cout << "Invalid choice. Please try again." << endl;
        }
    }

    return 0;
}
