![alt text](IMG/petctlbanner.png?raw=true)

# PETCTL

Это контролер управляющий станком преобразующим ленту нарезанную из PET бутылок в волокно пригодное для 3D печати.

![PETCTL assembled](PCB_V09_assembly/IMG/PETCTL_assembled.jpg)

Вот схема:

---

<img style="max-width:90%;height:auto" src="PCB/EU2TT/PETCTL_v0.9 diagram.png" alt="PETCTL scheme" />

**Спасибо** [EU2TT](https://github.com/EU2TT) за помощь в облагораживании и доработке схемы.

---

- В данный момент контроллер используется для управления [редуктором PETPull-2](https://drive.google.com/drive/mobile/folders/1PTYfURWS0YwCPlCB0__WyJwqnNEWJszi/1sBVlF62mEFIv8p1nZIAzGzY9kn1hc471/1dZt_md5HvzvhJHkd0jt-X09GqNWF04Xx/17iroY9sDo6CCnm7wmTta5178AHUz0zxp?usp=sharing&sort=13&direction=a)
- Нагревательный блок со стандартными нагревателем от принтера 24V 40W.
- Питается от принтерного же БП на 24V. Для получения 5V используется модуль TPS54560. Потому что он у меня валялся. Можно использовать что нибудь поскромнее но 7805 на падении 19V, наверное, "спечётся". Наверное, это всё будет работать и от 12V. 
- [Фюзер (сопло) моей конструкции](https://github.com/mvbasov/PETCTL/tree/github/3D_models/HeatedBlock)
- [Печатная плата от EU2TT](https://github.com/mvbasov/PETCTL/tree/github/PCB/EU2TT). Габариты 100 x 50 мм. SMD компоненты 0805. Если есть непреодолимое желание то можно натянуть 0603. Это бета версия платы не очень удобная для монтажа и впихивания в корпус. Возможно, будет улучшенная версия. Плата проверена и функционально полностью работоспособна. Под эту плату разработан [корпус](PCB_V09_assembly/3D_models) и написана [инструкция по сборке](PCB_V09_assembly/README.md)
- [Список подходящих компонентов](BOM.md)
- У меня нет желания, возможности и способностей создавать полноценный, хорошо повторяемый проект и поддерживать его как это [сделал уважаемый Zneipas](https://3deshnik.ru/forum/viewtopic.php?f=37&t=986), за что ему большое спасибо! Но на любые вопросы готов ответить, если будет не лень.
- Начальная схема предложена ɢᴇᴏʀɢɪʏ(@nehilo011)  но от неё уже осталось далеко не всё. Собственно, схема родилась из примеров от библиотек.
- Прошивка (скетч) на 90% состоит из [библиотек AlexGyver отсюда](https://alexgyver.ru/lessons/gyverlibs/) и [отсюда](https://github.com/AlexGyver/GyverLibs).

# Как управлять
Управление получилось очень удобное (для меня):
- один клик регулировка температуры. Подсвечивается целевая температура справа в углу. В этом режиме длинное нажатие включает/выключает нагреватель, загорается/гаснет звёздочка в начале 1-й строки.
- два клика регулировка скорости. Подсвечивается скорость в середине. В этом режиме длинное нажатие включает/выключает двигатель, загорается/гаснет звёздочка в начале 2-й строки.
- Если ничего не нажимать 15 секунд переходит в ждущий режим как на фото.
- Если подключен датчик окончания ленты то после его срабатывания двигатель выключается после протяжки CFG_PULL_EXTRA_LENGTH [м] нагрев, тоже, выключается
- Если подключен датчик обрыва волокна то после его срабатывания двигатель выключается мгновенно и нагрев, тоже, выключается

# вот так всё начиналось
<img style="max-width:75%;height:auto" src="PETCTL_screen.jpg" alt="Screen photo" />
