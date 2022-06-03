# SI_2022_lab2_151112

# Ina Lazarevska, 151112

  # Control Flow Graph
![SI_lab2 drawio](https://user-images.githubusercontent.com/103387343/171963528-7184147c-531b-4e4a-a2ce-4ffe8237106d.png)


import java.util.ArrayList;
import java.util.List;

public class SILab2 {

    public static List<String> function(List<String> list) {
        if (list.size() <= 0) { //A
            throw new IllegalArgumentException("List length should be greater than 0"); //B
        }
        int n = list.size();
        int rootOfN = (int) Math.sqrt(n); //C
        if (rootOfN * rootOfN  != n) { //D
            throw new IllegalArgumentException("List length should be a perfect square"); //E
        }
        List<String> numMines = new ArrayList<>(); //F
        for (int i = 0; i < n; i++) { //G
            if (!list.get(i).equals("#")) { //H
                int num = 0; //I
                if ( (i % rootOfN != 0 && list.get(i - 1).equals("#")) || (i % rootOfN != rootOfN - 1 && list.get(i + 1).equals("#")) ) { //G
                    if ( (i % rootOfN != 0 && list.get(i - 1).equals("#")) && (i % rootOfN != rootOfN - 1 && list.get(i + 1).equals("#")) ){ //K
                        num += 2; //L
                    }
                    else {
                        num  += 1; //M
                    }
                }
                if (i - rootOfN >= 0 && list.get(i - rootOfN).equals("#")){ //N
                    num++; //O
                }
                if (i + rootOfN < n && list.get(i + rootOfN).equals("#")){ //P
                    num++; //Q
                }
                numMines.add(String.valueOf(num)); //R
            }
            else {
                numMines.add(list.get(i)); //S
            }
        }
        return numMines; //T
    }
}
