Task-1:

Suppose you are working on a geometry library that deals with different types of geometric shapes, including circles, rectangles, and triangles. 
Each shape has common properties like area and perimeter, but also specific attributes such as radius for circles, length and width for rectangles, and side lengths for triangles.

•	Develop a class hierarchy for geometric shapes using inheritance in C++.
•	Explain how you would utilize inheritance and polymorphism to implement algorithms for calculating area and perimeter that are specific to each type of shape

#include <iostream>
#include <cmath>

// Base class for geometric shapes
class Shape {
public:
    // Virtual functions for area and perimeter
    virtual double area() const = 0;
    virtual double perimeter() const = 0;
};

// Circle class derived from Shape
class Circle : public Shape {
private:
    double radius;
public:
    // Constructor
    Circle(double r) : radius(r) {}
    
    // Overrides for area and perimeter
    double area() const override {
        return M_PI * radius * radius;
    }
    
    double perimeter() const override {
        return 2 * M_PI * radius;
    }
};

// Rectangle class derived from Shape
class Rectangle : public Shape {
private:
    double length;
    double width;
public:
    // Constructor
    Rectangle(double l, double w) : length(l), width(w) {}
    
    // Overrides for area and perimeter
    double area() const override {
        return length * width;
    }
    
    double perimeter() const override {
        return 2 * (length + width);
    }
};

// Triangle class derived from Shape
class Triangle : public Shape {
private:
    double side1;
    double side2;
    double side3;
public:
    // Constructor
    Triangle(double s1, double s2, double s3) : side1(s1), side2(s2), side3(s3) {}
    
    // Overrides for area and perimeter
    double area() const override {
        double s = (side1 + side2 + side3) / 2;
        return sqrt(s * (s - side1) * (s - side2) * (s - side3));
    }
    
    double perimeter() const override {
        return side1 + side2 + side3;
    }
};

int main() {
    // Example usage
    Circle circle(5);
    Rectangle rectangle(4, 6);
    Triangle triangle(3, 4, 5);
    
    std::cout << "Circle: Area = " << circle.area() << ", Perimeter = " << circle.perimeter() << std::endl;
    std::cout << "Rectangle: Area = " << rectangle.area() << ", Perimeter = " << rectangle.perimeter() << std::endl;
    std::cout << "Triangle: Area = " << triangle.area() << ", Perimeter = " << triangle.perimeter() << std::endl;
    
    return 0;
}

Task-2:

An operator overloading allows custom behavior to be defined for built-in operators like addition (+), subtraction (-), when we used with user-defined types.
When overloading binary operators as friend functions, external functions can access private members of a class.
Provide examples how binary operator overloading is implemented using friend functions. 
#include <iostream>

class Complex {
private:
    double real;
    double imag;
public:
    // Constructor
    Complex(double r = 0.0, double i = 0.0) : real(r), imag(i) {}
    
    // Getter functions
    double getReal() const { return real; }
    double getImag() const { return imag; }
    
    // Overloading binary addition operator (+) as a friend function
    friend Complex operator+(const Complex& c1, const Complex& c2);
};

// Definition of overloaded addition operator
Complex operator+(const Complex& c1, const Complex& c2) {
    return Complex(c1.real + c2.real, c1.imag + c2.imag);
}

int main() {
    Complex a(3.0, 4.0);
    Complex b(1.5, 2.5);
    
    Complex c = a + b; // Uses overloaded addition operator
    
    std::cout << "Result of addition: " << c.getReal() << " + " << c.getImag() << "i" << std::endl;

    return 0;
}


