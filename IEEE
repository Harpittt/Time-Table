#include <iostream>
#include <vector>
#include <algorithm>

struct Course {
    std::string code;
    int credits;
};

struct Slot {
    std::string name;
    std::string type;
    std::vector<Course> courses;
    int capacity;
};

bool compare_courses(const Course& c1, const Course& c2) {
    return c1.credits > c2.credits;
}

bool compare_slots(const Slot& s1, const Slot& s2) {
    if (s1.type != s2.type) {
        return s1.type < s2.type;
    } else {
        return s1.capacity > s2.capacity;
    }
}

int main() {
    int num_courses, num_slots;
    std::cout << "Enter the number of courses: ";
    std::cin >> num_courses;
    std::vector<Course> courses(num_courses);

    for (int i = 0; i < num_courses; ++i) {
        std::cout << "Enter the code of course " << i+1 << ": ";
        std::cin >> courses[i].code;
        std::cout << "Enter the credits of course " << i+1 << ": ";
        std::cin >> courses[i].credits;
    }

    std::cout << "Enter the number of slots: ";
    std::cin >> num_slots;
    std::vector<Slot> slots(num_slots);

    for (int i = 0; i < num_slots; ++i) {
        std::cout << "Enter the name of slot " << i+1 << ": ";
        std::cin >> slots[i].name;
        std::cout << "Enter the type of slot " << i+1 << " (A, B, C,D): ";
        std::cin >> slots[i].type;
        std::cout << "Enter the capacity of slot " << i+1 << ": ";
        std::cin >> slots[i].capacity;
    }

    // Sort the courses by credits in descending order
    std::sort(courses.begin(), courses.end(), compare_courses);

    // Sort the slots by type and then capacity in descending order
    std::sort(slots.begin(), slots.end(), compare_slots);
    std::cout << "Credits for: A=4 B=3 C=2 D=1 ";

    // Allocate courses to slots
    int course_idx = 0;
    for (auto& slot : slots) {
        while (slot.courses.size() < slot.capacity && course_idx < num_courses) {
            if (slot.type == "A" && courses[course_idx].credits <= 4) {
                slot.courses.push_back(courses[course_idx]);
                ++course_idx;
            } else if (slot.type == "B" && courses[course_idx].credits == 3) {
                slot.courses.push_back(courses[course_idx]);
                ++course_idx;
            } else if (slot.type == "C" && courses[course_idx].credits == 2) {
                slot.courses.push_back(courses[course_idx]);
                ++course_idx;
            } else if (slot.type == "D" && courses[course_idx].credits == 1) {
                slot.courses.push_back(courses[course_idx]);
                ++course_idx;
            } else {
                ++course_idx;
            }
        }
    }

    // Print the timetable
    std::cout << "\nTimetable:\n";
    for (const auto& slot : slots) {
        std::cout << slot.name << " (" << slot.type << "):" << std::endl;
        for (const auto& course : slot.courses) {
            std::cout << "\t" << course.code << " (credits: " << course.credits << ")" << std::endl;
        }
    }

    return 0;
}
