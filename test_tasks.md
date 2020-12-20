# Test from 19 of December

+ [Complex Numbers class](#complex-numbers-class)
+ [Enum currency](#enum-currency)
+ [Enum Ancestor](#enum-ancestor)

## Complex Numbers class

```java
import java.util.Comparator;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class ComplexNum {
    double real;
    double imaginary;
    
    public ComplexNum (double real, double imaginary){
        this.real = real;
        this.imaginary = imaginary;
    }
    
    double getReal(){
        return real;
    }
    double getImaginary(){
        return imaginary;
    }
    
    double getMod() {
        return Math.sqrt(this.real * this.real + this.imaginary * this.imaginary);
    }
    public static ComplexNum sum(ComplexNum num1, ComplexNum num2){
        return new ComplexNum(num1.getReal() + num2.getReal(), num1.getImaginary() + num2.getImaginary());
    }
    public static ComplexNum subtract(ComplexNum num1, ComplexNum num2){
        return new ComplexNum(num1.getReal() - num2.getReal(), num1.getImaginary() - num2.getImaginary());
    }
    public static ComplexNum multiply(ComplexNum num1, ComplexNum num2) {
        return new ComplexNum(num1.getReal() * num2.getReal() - num1.getImaginary() * num2.getImaginary(), num1.getReal() * num2.getImaginary() + num1.getImaginary() * num2.getReal());
    }
    
    public class CompareComplexNum {
        public static Comparator<ComplexNum> SORT_BY_MOD = new Comparator<ComplexNum>() {
            @Override
            public int compare(ComplexNum x, ComplexNum y) {  
                return x.getMod() - y.getMod();
            }
        };
    }
    
    public List<ComplexNum> sortNums(List<ComplexNum> nums) {
        return Collections.sort(nums, ComplexNum.SORT_BY_MOD);
    }
}

```

## Enum currency

```java
public enum Currency {

    DOLLAR ("dollar"),
    EURO ("euro"),
    YUAN ("yuan"),
    RUBLE ("ruble");
    
    private String name;

    Currency(String name) {
        this.name = name;
    }

}
```

## Enum Ancestor

```java
public class Currency {
    
    private String name;
    Currency(String name) {
        this.name = name;
    }
    
    public static Currency DOLLAR = new Currency("dollar");
    public static Currency EURO = new Currency("euro");
    public static Currency YUAN = new Currency("yuan");
    public static Currency RUBLE = new Currency("ruble");
}
```