# Array-5

## Problem1: Bind Robot in a Circle (https://leetcode.com/problems/robot-bounded-in-circle/)

class Solution {
public:
    bool isRobotBounded(string s) {
        int dir = 0;
        int x = 0, y= 0;
        int i, n = s.size();
        for(i=0;i<n;i++){
            char path = s[i];
            if (path == 'L'){
                dir = (dir + 3)%4;
            }
            else if(path == 'R'){
                dir = (dir+1)%4;
            }
            else {
                if(dir == 0)
                    y++;
                else if (dir==1)
                    x++;
                else if(dir == 3)
                    x--;
                else 
                    y--;
            }
        }
        if(dir== 0 && (x!=0 || y!= 0))  // dono (x & y) hii change honge tabhi false
            return false;
        return true;
    }
};

## Problem2: Calculate Tax

 Write a program to calculate tax if Salary and Tax Brackets are given as list in the form [ [10000, .3],[20000, .2], [30000, .1], [None, .1]]. You don’t know in the beginning how many tax brackets are there. You have to test for all of them 
 
 class GFG {

	public static void main (String[] args) {

		List<List<Double>> levels = new ArrayList<>();

        levels.add( Arrays.asList(10000.0, 0.3) );

        levels.add( Arrays.asList(20000.0, 0.2) );

        levels.add( Arrays.asList(30000.0, 0.1) );

        levels.add( Arrays.asList(null, 0.1) );

        double tax = calculateTax(levels,45000);

        System.out.println(tax);

	}

	public static double calculateTax(List<List<Double>> levels, double salary ){


    }

}


O(n) time

import java.io.*;

import java.util.*;



class GFG {

	public static void main (String[] args) {

		List<List<Double>> levels = new ArrayList<>();

        levels.add( Arrays.asList(10000.0, 0.3) );

        levels.add( Arrays.asList(20000.0, 0.2) );

        levels.add( Arrays.asList(30000.0, 0.1) );

        levels.add( Arrays.asList(null, 0.1) );

        double tax = calculateTax(levels,45000);

        System.out.println(tax);

	}

	public static double calculateTax(List<List<Double>> levels, double salary ){

        return helper(salary, 0, 0, levels, 0);     

    }

    private static double helper(double salary, double prev, double tax, List<List<Double>> levels, int index){

        // base 

        if(salary < 0) return tax;

        List<Double> le = levels.get(index);

        double percent = le.get(1);

        if(le.get(0) == null) return tax + percent * salary;

        double currentTaxable = Math.min(le.get(0) - prev, salary);

        tax += currentTaxable*percent;

        salary -= currentTaxable;

        prev = le.get(0);

        return helper(salary,prev, tax,levels,index+1);

    }

}

Iterative

O(n) time

/*package whatever //do not write package name here */



import java.io.*;

import java.util.*;



class GFG {

	public static void main (String[] args) {

		List<List<Double>> levels = new ArrayList<>();

        levels.add( Arrays.asList(10000.0, 0.3) );

        levels.add( Arrays.asList(20000.0, 0.2) );

        levels.add( Arrays.asList(30000.0, 0.1) );

        levels.add( Arrays.asList(null, 0.1) );

        double tax = calculateTax(levels,45000);

        System.out.println(tax);

	}

	public static double calculateTax(List<List<Double>> levels, double salary ){

        double left = salary;

        double tax = 0;

        double limit=0;

        int i = 0;

        while(left > 0){

            List<Double> level = levels.get(i);

            double percent = level.get(1);

            if(level.get(0)==null){

                tax += left*percent;

                return tax;

            }

            double currRange = level.get(0) - limit;

            double currSalary = Math.min(left, currRange);

            tax += currSalary*percent;

            left -= currSalary;

            limit = level.get(0);

            i++;

        }

        return tax;        

    }

}

