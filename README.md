# Google Test Example
```cmake
# google test
include(FetchContent)
FetchContent_Declare(
        googletest
        URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)


## testing
enable_testing()

add_executable(
        hello_test
        hello_test.cc
)
target_link_libraries(
        hello_test
        GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(hello_test)
```

## Quick Start
1. Add scripts to `CmakeLists.txt`
    ```cmake
    # google test
    include(FetchContent)
    FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
    )
    # For Windows: Prevent overriding the parent project's compiler/linker settings
    set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
    FetchContent_MakeAvailable(googletest)


    ## testing
    enable_testing()

    add_executable( # TODO: Change this
    hello_test  
    hello_test.cc
    )
    target_link_libraries(
    hello_test  # TODO: Change this
    GTest::gtest_main
    )

    include(GoogleTest)
    gtest_discover_tests(hello_test)  # TODO: Change this
    ```
2. Add test file(e.g. `hello_test.cc`)
    ```c++
   #include <gtest/gtest.h>

    // Demonstrate some basic assertions.
    TEST(HelloTest, BasicAssertions) {
    // Expect two strings not to be equal.
    EXPECT_STRNE("hello", "world");
    // Expect equality.
    EXPECT_EQ(7 * 6, 42);
    }
   ```
3. Build and test
    ```shell
    cmake -S . -B build
    cmake --build build
    cd build && ctest
    ```

## Reference
- [GoogleTest(Cmake)](https://google.github.io/googletest/quickstart-cmake.html)
- [Korean document for CLion](https://jahong.tistory.com/entry/C-%ED%85%8C%EC%8A%A4%ED%8A%B8-%ED%99%98%EA%B2%BD-%EA%B5%AC%EC%B6%95-CLion%EC%97%90%EC%84%9C-Google-Test-%EC%97%B0%EB%8F%99-%EC%82%AC%EC%9A%A9-%EB%B0%A9%EB%B2%95with-cmake)
