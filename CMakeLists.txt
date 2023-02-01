#cmake_minimum_required(VERSION 3.5)

#project(ForMarbleTest LANGUAGES CXX)

#set(CMAKE_CXX_STANDARD 11)
#set(CMAKE_CXX_STANDARD_REQUIRED ON)

#add_executable(ForMarbleTest main.cpp)


# стандартная шапка
cmake_minimum_required ( VERSION 3.10.2 )
project(ForMarbleTest)

# указываем в нашем проекте где лежат дополнительные .cmake файлы
LIST(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake" "${PROJECT_SOURCE_DIR}/import/cmake")

# выполняем поиск marble-библиотеки, см. выше файл FindMarble.cmake
find_package(Marble)
if (Marble_FOUND)
  message( STATUS "Marble includes: ${Marble_INCLUDE_DIR}")
  message( STATUS "Marble libraries: ${Marble_LIBRARIES}")
else()
  message(WARNING "Not found Marble!")
endif()

# настраиваем includes
include_directories("${Marble_INCLUDE_DIR}")  # заголовочные файлы marble-библиотеки
# создаём приложение
add_executable(ForMarbleTest main.cpp)
# подключаем к приложению библиотеку marble
target_link_libraries(ForMarbleTest ${Marble_LIBRARIES})
