#include <iostream>
#include <string>

class Overcoat {
private:
    std::string type;
    double price;

public:
    Overcoat(const std::string& t = "", double p = 0.0) : type(t), price(p) {}
    bool operator==(const Overcoat& other) const {
        return type == other.type;
    }

    Overcoat& operator=(const Overcoat& other) {
        if (this != &other) {
            type = other.type;
            price = other.price;
        }
        return *this;
    }

    bool operator>(const Overcoat& other) const {
        if (type == other.type) {
            return price > other.price;
        }
        return false;
    }

    void display() const {
        std::cout << "Type: " << type << ", Price: " << price << std::endl;
    }
};

class Flat {
private:
    double area;
    double price;

public:
    Flat(double a = 0.0, double p = 0.0) : area(a), price(p) {}
    bool operator==(const Flat& other) const {
        return area == other.area;
    }

    Flat& operator=(const Flat& other) {
        if (this != &other) {
            area = other.area;
            price = other.price;
        }
        return *this;
    }

    bool operator>(const Flat& other) const {
        return price > other.price;
    }

    void display() const {
        std::cout << "Area: " << area << ", Price: " << price << std::endl;
    }
};

int main() {
    Overcoat coat1("Winter", 150.0);
    Overcoat coat2("Winter", 200.0);
    Overcoat coat3("Summer", 100.0);

    std::cout << "Coat1: ";
    coat1.display();
    std::cout << "Coat2: ";
    coat2.display();

    std::cout << "Coat1 == Coat2: " << (coat1 == coat2 ? "True" : "False") << std::endl;
    std::cout << "Coat1 > Coat2: " << (coat1 > coat2 ? "True" : "False") << std::endl;

    coat1 = coat3;
    std::cout << "After assignment, Coat1: ";
    coat1.display();

    Flat flat1(50.0, 100000.0);
    Flat flat2(60.0, 120000.0);
    Flat flat3(50.0, 90000.0);

    std::cout << "\nFlat1: ";
    flat1.display();
    std::cout << "Flat2: ";
    flat2.display();

    std::cout << "Flat1 == Flat3: " << (flat1 == flat3 ? "True" : "False") << std::endl;
    std::cout << "Flat2 > Flat1: " << (flat2 > flat1 ? "True" : "False") << std::endl;

    flat1 = flat2;
    std::cout << "After assignment, Flat1: ";
    flat1.display();

    return 0;
}
