#include <iostream>
#include <string>
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <dirent.h>

using namespace std;

void list_files(const string& path) {
    DIR* dir;
    struct dirent* entry;

    if ((dir = opendir(path.c_str())) == NULL) {
        cout << "No files found or directory does not exist.\n";
        return;
    }
  while ((entry = readdir(dir)) != NULL) {
        if (entry->d_type != DT_DIR) {  
            cout << entry->d_name << endl;
        }
    }
    closedir(dir);
    }
    }
void list_files_by_extension() {
    string extension;
    cout << "Enter file extension (e.g., .txt): ";
    cin >> extension;
    cin.ignore();

    string path = ".";
    DIR* dir;
    struct dirent* entry;

if ((dir = opendir(path.c_str())) == NULL) {
        cout << "No files found or directory does not exist.\n";
        return;
    }

    while ((entry = readdir(dir)) != NULL) {
        string filename = entry->d_name;
        if (filename.find(extension) != string::npos && entry->d_type != DT_DIR) {
            cout << filename << endl;
        }

void list_files_by_name() {
    string name;
    cout << "Enter file name (use * as wildcard, e.g., *.txt): ";
    cin >> name;
    cin.ignore();

