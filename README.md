После того, как вы настроили взаимодействие с системой непрерывной интеграции,
обеспечив автоматическую сборку и тестирование ваших изменений, стоит задуматься
о создание пакетов для измениний, которые помечаются тэгами (см. вкладку releases).
Пакет должен содержать приложение solver из предыдущего задания Таким образом, каждый новый релиз будет состоять из следующих компонентов:

архивы с файлами исходного кода (.tar.gz, .zip)
пакеты с бинарным файлом solver (.deb, .rpm, .msi, .dmg)
В качестве подсказки:
```
$ cat .travis.yml
os: osx
script:
...
- cpack -G DragNDrop # dmg

$ cat .travis.yml
os: linux
script:
...
- cpack -G DEB # deb

$ cat .travis.yml
os: linux
addons:
  apt:
    packages:
    - rpm
script:
...
- cpack -G RPM # rpm

$ cat appveyor.yml
platform:
- x86
- x64
build_script:
...
- cpack -G WIX # msi
```
