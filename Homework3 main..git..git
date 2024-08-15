
import java.util.*;



public  class dotsAndCrosses  {

   public final int SIZE = 5; //размер поля
   public final char DOT_X = 'X'; //игрок
   public final char DOT_O = 'O'; //ИИ
    public final char DOT_EMPTY = '.'; //пустая ячейка
    char[][] map = new char[SIZE][SIZE];
    Scanner sc = new Scanner(System.in);
    Random rand = new Random();

    public static void main (String[] args) {
        new dotsAndCrosses().startGame();
    }

   public void startGame() { //запуск игры
       System.out.println("Перед вами игровое поле");
        initMap();
       printMap();
       System.out.println("В игре задействована 5 строк(X) и 5 столбов(Y):");
        while (true) {
            humanTurn();
            printMap();
            if (checkWin(DOT_X)) {
                System.out.println("Поздравляю, вы победили!");
                break;
            }
            if (isMapFull()) {
                System.out.println("Ничья!");
                break;
            }
            aiTurn();
            printMap();
            if (checkWin(DOT_O)) {
                System.out.println("Компьютер победил!");
                break;
            }
            if (isMapFull()) {
                System.out.println("Ничья!");
                break;
            }
        }
        System.out.println("Игра окончена!");
    }

    public void initMap() {
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {// инициализация и циклы заполнение игрового поля точками
                map[i][j] = DOT_EMPTY;
            }
        }
    }

    public void humanTurn() { //ход человека
        int x, y;
        do {
            System.out.println("Ваш ход, введите координаты X и Y:");
            x = sc.nextInt() - 1;
            y = sc.nextInt() - 1;
        } while (!isCellValid(x, y));
        map[x][y] = DOT_X;
    }

    public void aiTurn() { //ход ИИ
        System.out.println("Ход компьютера");
        int x, y;
        do {
            x = rand.nextInt(SIZE);
            y = rand.nextInt(SIZE);
        } while (!isCellValid(x, y));//проверка на то, что поле пустое, если нет - цикл будет работать дальше.
        Random rand = new Random();
        int blockingNumber = rand.nextInt(10);// создание случайного числа для активации усиления ИИ

        if(blockingNumber > 3){// если сл. число соответствует условиям - усилививаем логику ИИ
            int m = 0;// для закрытия цикла while
            first:// метка
        while(m < 1) {
            int diag1, diag2, hor, ver;// создание переменных


            for (int i = 0; i < SIZE; i++) {// цикл проверки для блокировки игрока по горизонтали и вертикали
                hor = 0;
                ver = 0;
                for (int j = 0; j < SIZE; j++) {
                    if (map[i][j] == DOT_X) {
                        hor++;
                        if (hor == 3 && j < SIZE - 1) {// если компьютер высчитывает что игрок близок к победе, ходит так, чтобы сбить победу
                            map[i][j + 1] = DOT_O;

                                break first; // выход из блока second

                        }
                    }
                    if (map[j][i] == DOT_X) {
                        ver++;
                        if (ver == 3 && j < SIZE - 1) {// если компьютер высчитывает что игрок близок к победе, ходит так, чтобы сбить победу
                            map[j + 1][i] = DOT_O;

                                break first; // выход из блока second

                        }
                    }
                }

            }
            diag1 = 0;// Логика блокировки диагоналей выполнена менее совершенна, хотя я знаю как это можно было бы сделать с около 100%-ой вероятностью
            diag2 = 0;// тем не менее она работает, и я решил не заморачиваться особо так как итак вполне неплохо, кроме того сказали что это делать не обязательно
            // вот я не доделываю.
            boolean t2 = true;
            second:
            for (int i = 0; i < SIZE; i++) {// цикл проверки для блокировки игрока по диагоналям
                if (map[i][i] == DOT_X) {
                    diag1++;
                    if (diag1== 3 && i < SIZE + 1) {// если компьютер высчитывает что игрок близок к победе, ходит так, чтобы сбить победу
                        map[i + 1][i + 1] = DOT_O;

                            break second; // выход из блока second

                    }
                }
                if (map[i][SIZE - i - 1] == DOT_X) {
                    diag2++;
                    if (diag2== 3 && i < SIZE - 1) {// если компьютер высчитывает что игрок близок к победе, ходит так, чтобы сбить победу
                        map[i - 1][SIZE - i - 2] = DOT_O;

                        break second; // выход из блока second

                    }
                i++;
            }

        }
            m++;
    }
            map[x][y] = DOT_O;

        }
        else map[x][y] = DOT_O;
        System.out.println("Компьютер походил в точку " + (x + 1) + " " + (y + 1));
}




    public void printMap() { //вывод поля в консоль
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE;j++) {
                System.out.print(map[i][j] + " ");//расспечатка поля
            }
            System.out.println();// переход на следующую строку поля
        }
        System.out.println();
    }


    public boolean checkWin(char dot) { //проверка победы
        int diag1, diag2, hor, ver;//инициализация  переменных диагональных и вертикальных и горизонтальных
        for (int i = 0; i < SIZE; i++) { //проход по игровому полю для определения положений
            hor = 0; ver = 0;
            for (int j = 0; j < SIZE; j++) {
                if (map[i][j] == dot) {// подсчет горизонтальных рядов и сохранение результата в переменнею hor
                    hor++;
                }
                else if (map[i][j] != dot){
                    hor--;
                }
                if (map[j][i] == dot ) {// подсчет вертикальных рядов и сохранение результата в переменнею ver
                    ver++;
                }
                else if (map[j][i] != dot){
                    ver--;
                }
                if (hor == 4|| ver == 4) {
                    return true; //проверка по горизонтали и вертикали и воззврат результата
                }
            }

        }
        diag1 = 0; diag2 = 0;
        for (int i = 0; i < SIZE; i++) {
            if (map[i][i] == dot) {
                diag1++;
            }
            else if (map[i][i] != dot){
                diag1--;
            }
            if (map[i][SIZE - i - 1] == dot) {
                diag2++;
            }
            else if  (map[i][SIZE - i - 1] != dot) {
                diag2--;
            }
            if (diag1 == 4 || diag2 == 4) {
                return true; //проверка по диагоналям
            }
        }

        return false;
    }

    public boolean isMapFull() { //проверка на заполненность поля
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                if (map[i][j] == DOT_EMPTY) return false;// вернуть false если есть пустые клетки
            }
        }
        return true;// вернуть true если пустых клеток нет
    }

    public boolean isCellValid(int x, int y) { //поиск свободной ячейки
        if (x < 0 || y < 0 || x >= SIZE || y >= SIZE) return false;
        if (map[x][y] == DOT_EMPTY) return true;
        return false;
    }
}
