рабочая:
#include <iostream>
#include <vector>
#include <queue>
#include <ctime>
#include <cstdlib>

bool Find(std::vector<std::vector<int>>& matrix, int startX, int startY) {
    int n = matrix.size();
    
    if (startX < 0 || startX >= n || startY < 0 || startY >= n || matrix[startX][startY] == 0) {
        return false;
    }

    if (startX == n - 1) {
        return true;
    }

    matrix[startX][startY] = 0;
    
    if (Find(matrix, startX + 1, startY)) return true;
    if (Find(matrix, startX - 1, startY)) return true;
    if (Find(matrix, startX, startY + 1)) return true;
    if (Find(matrix, startX, startY - 1)) return true;
    
    return false;
}

int main() {
    std::srand(std::time(0));
    int m;
    std::cin >> m;
    std::vector<std::vector<int>> matrix(m, std::vector<int>(m));

    for (int i = 0; i < m; i++) {
        for (int j = 0; j < m; j++) {
            matrix[i][j] = std::rand() % 2;
        }
    }

    for (int i = 0; i < m; i++) {
        for (int j = 0; j < m; j++) {
            std::cout << matrix[i][j] << " ";
        }
        std::cout << std::endl;
    }

            int a=0;
    for (int startY = 0; startY < m; startY++) {
        std::vector<std::vector<int>> tempMatrix = matrix;

        if (Find(tempMatrix, 0, startY)) {
            //std::cout << "true ";
            a++;
            
        } else {
            //std::cout << "false ";
        }
    }
    if (a>0)
    std::cout << "true ";
    else 
    std::cout << "false ";
    std::cout << std::endl;
    
    return 0;
}


=================================================================================
#include <iostream>
#include <vector>
#include <queue>
#include <ctime>
#include <cstdlib>

bool Find(std::vector<std::vector<int>>& matrix,  int x , int y) {
    int n = matrix.size();

        if (y == n - 1) {
            return true;
        }
        if (x < 0 || x >= n || y < 0 || y >= n || matrix[x][y] == 0) {
            return false;
        }


        matrix[x][y] = 0;


        if (Find(matrix, x + 1, y)) return true;
        if (Find(matrix, x - 1, y)) return true;
        if (Find(matrix, x, y + 1)) return true;
        if (Find(matrix, x, y - 1)) return true;

    return false;
}

int main() {
    std::srand(std::time(0));
    int m;
    std::cin >> m;
    std::vector<std::vector<int>> matrix(m, std::vector<int>(m));

    for (int i = 0; i < m; i++) {
        for (int j = 0; j < m; j++) {
            matrix[i][j] = std::rand() % 2;
        }
    }

    for (int i = 0; i < m; i++) {
        for (int j = 0; j < m; j++) {
            std::cout << matrix[i][j] << " ";
        }
        std::cout << std::endl;
    }

    int n = matrix.size();
    int y = 0;


    for (int x1 = 0; x1 < n ; x1++)
    {
        Find(matrix, x1,0);


        if (Find(matrix,x1,0)) {
            std::cout << "true ";
        }
        else {
            std::cout << "false ";
        }
    }
    return 0;
}
===================================================================================================









#include <iostream>
#include <vector>
#include <queue>
#include <ctime>
#include <cstdlib>
#include <fstream>

bool Find(std::vector<std::vector<int>>& matrix, int x = 0, int y = 0) {
    int n = matrix.size();

    if (x < 0 || x >= n || y < 0 || y >= n || matrix[x][y] == 0) {
        return false;
    }
    if (x == n - 1 && y == n - 1) {
        return true;
    }
    matrix[x][y] = 0;

    if (Find(matrix, x + 1, y)==true) return true;
    if (Find(matrix, x - 1, y)==true) return true;
    if (Find(matrix, x, y + 1)==true) return true;
    if (Find(matrix, x, y - 1)==true) return true;

    return false;
}

int main() {
    std::srand(std::time(0));
    int m;
    std::cin >> m;


    std::vector<std::vector<int>> matrix(m, std::vector<int>(m));

    std::vector<int> freq(100, 0);


    for (int n = 0; n < 100; n++) {
        for (int p = 0; p < 1000; p++) {

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < m; j++) {
                matrix[i][j] = std::rand() % 100;
            }
        }

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < m; j++) {
                if (matrix[i][j] <= n)
                    matrix[i][j] = 1;
                else matrix[i][j] = 0;
            }
        }

        if (Find(matrix) == true) {
            freq[n]++;
        }
    }

    }        
    for (int i = 0; i < 100; i++) {
            std::cout << freq[i];
            std::cout << " ";
        }
    std::ofstream out;         
    out.open("C:\\Users\\test2023\\Desktop\\gg\\.vs\\gg\\v17\\ConsoleApplication1\\ConsoleApplication1\\gg.txt");      
    if (out.is_open())
    {
        for (int i = 0; i < 100; i++) {

            out << freq[i] << '\n';
        }
    }
    out.close();

    return 0;
}
