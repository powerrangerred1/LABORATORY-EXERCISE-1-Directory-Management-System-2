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

