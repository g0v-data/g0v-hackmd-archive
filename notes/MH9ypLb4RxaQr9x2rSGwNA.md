```
#include <iostream>
#include <string>
#include <boost/multi_index_container.hpp>
#include <boost/multi_index/hashed_index.hpp>
#include <boost/multi_index/member.hpp>
#include <boost/functional/hash.hpp>

struct MyStruct {
    std::string name;
    int value;
};

// 自定義的 hash function
struct MyHashFunction {
    std::size_t operator()(const std::string& str) const {
        std::size_t seed = 0;
        for (char c : str) {
            boost::hash_combine(seed, c);
        }
        return seed;
    }
};

// 定義 hashed_unique index 的 key 為 name，並使用自定義的 hash function
struct Name {};

// 定義 multi_index_container
typedef boost::multi_index_container<
    MyStruct,
    boost::multi_index::indexed_by<
        boost::multi_index::hashed_unique<
            boost::multi_index::tag<Name>,
            BOOST_MULTI_INDEX_MEMBER(MyStruct, std::string, name),
            boost::hash<MyHashFunction>
        >
    >
> MyContainer;

int main() {
    MyContainer myContainer;

    // 插入一些元素
    myContainer.insert({ "apple", 1 });
    myContainer.insert({ "banana", 2 });
    myContainer.insert({ "orange", 3 });

    // 使用索引查找元素
    auto& nameIndex = myContainer.get<Name>();
    auto it = nameIndex.find("banana");
    if (it != nameIndex.end()) {
        std::cout << "Found: " << it->name << ": " << it->value << std::endl;
    } else {
        std::cout << "Not found" << std::endl;
    }

    return 0;
}

```