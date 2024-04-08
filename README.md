## <a id="faq">Что такое SCP: Secret Lab?</a>
[SCP: Secret Laboratory](https://scpslgame.com/) это бесплатный многопользовательский хоррор на основе серии SCP Foundation и ее расширенной вселенной монстров и паранормальных явлений.

От находчивых D-классов и хитроумных ученых до элитных подразделений боевых групп, мятежных Повстанцев Хаоса, и даже ужасные объекты SCP, в этой ужасной ситуации найдется немало ключевых ролей.

Испытайте на своей шкуре все равзнообразие Обьектов SCP крушащих все на своем пути, Повстанцев Хаоса саботирующих Фонд, МОГ и службы охраны мобилизующихся для обеспечения безопасности этого объекта, вооруженных ученых и узников класса D, пытающихся сбежать.

- [Что такое SCP: Secret Lab?](#faq)
    - [Минимальные системные требования](#SystemRequirements)
    - [Инструкции для Linux (Ubuntu/Debian)](#Instructions)
    - [Создание нового пользователя](#Createanewuser)
    - [Установка SCP:SL сервера с помощью SteamCMD](#SteamCMD)
    - [Конфигурация сервера](#Configuration)
    - [Верификация](#Verification)
- [Обозреватель серверов](#ServerExplorer)
    - [Модерирование сервера](#Servermoderation)
- [EXILED - библиотека для разработки плагинов](#Exiled)
    - [Установка EXILED](#EXILEDInstallation)
    - [Конфигурация](#EXILEDConfiguration)
    - [Для разработчиков](#Fordevelopers)

## <a id="SystemRequirements">Минимальные системные требования</a>
- 3 ГБ ОЗУ
- Intel Core i3, 2 потока, 2 ГГц
- 4 ГБ свободного места

## <a id="Instructions">Инструкции для Linux (Ubuntu/Debian)</a>

### Требования
- Заранее настроенный сервер с доступом по SSH и FTP

### Установка компонентов
**Mono** - Фреймворк, используемый Unity. Необходим для исправления проблем с голосовым чатом
- [Инструкции для Ubuntu](https://www.mono-project.com/download/stable/#download-lin-ubuntu)
- [Инструкции для Debian](https://www.mono-project.com/download/stable/#download-lin-debian)

**screen** - Позволяет запускать несколько окон в одной сессии, в нашем случае позволяет держать сервер без необходимости быть авторизованным.
```
sudo apt-get install screen
```
**SteamCMD** - Используется для установки и обновления сервера
```
sudo add-apt-repository multiverse
sudo apt-get install steamcmd
```
> Команда `sudo add-apt-repository multiverse` используется в операционных системах на базе Ubuntu для добавления репозитория `multiverse` в список источников пакетов.

>Репозиторий `multiverse` содержит программное обеспечение, которое не может быть полностью поддерживаемым Ubuntu из-за проблем с лицензиями, законодательства об авторских правах или других причинах. Если вы хотите иметь доступ к программному обеспечению из этого репозитория, вам придется добавить его в список источников.

## <a id="Createanewuser">Создание нового пользователя</a>
Новый пользователь будет создан специально для SCP:SL сервера, т.к. использование root пользователя небезопасно.
```
sudo adduser scpserver
```
> Создает нового пользователя с названием "scpserver"
```
su - scpserver
```
> Изменяет активного пользователя на "scpserver"

## <a id="SteamCMD">Установка SCP:SL сервера с помощью SteamCMD</a>
> SteamCMD используется для установки SCP:SL сервера в определенную директорию, а также упростит обновление сервера в будущем.

**Запуск SteamCMD** Необходимо для ввода последующих команд для установки сервера. Необходимо ввести следующую команду в директории SteamCMD.
```
./steamcmd.sh
```

### Изменение пути установки
Для того, чтобы установить сервер в определённую директорию:
```
force_install_dir <directory>
```
> пример: `force_install_dir /home/scpserver`

### Авторизация
Для того, чтобы скачать сервер, вы должны авторизоваться в Steam.
```
login anonymous
```
> Вы также можете войти с помощью аккаунта Steam, но это не является обязательным.

### Установка
Для установки сервера используется ID **996560**, это специальная сборка SCP:SL, которая будет работать эффективнее, чем если бы создать сервер в самой игре.
```
app_update 996560
```

### Проверка
Убедитесь, что все необходимые файлы загрузились правильно и не повреждены
```
app_update 996560 validate
```

## Запуск сервера
На Linux процедура запуска сервера немного отличается от Windows.
```
screen -S scpsl_server
```
> Создание новой сессии с названием "scpsl_server"
```
cd <directory>
```
> Переход в директорию сервера
```
./LocalAdmin 7777
```
> Запуск сервера при помощи LocalAdmin на порте 7777

## <a id="Configuration">Конфигурация сервера</a>
После установки сервер может быть настроен, и такие настройки, как название сервера, информация, лимит игроков и подобные могут быть изменены.

Все эти настройки могут быть изменены в файле **config_gameplay.txt**.
- Windows: `%AppData%\Roaming\SCP Secret Laboratory\config\<port>\config_gameplay.txt`
- Linux: `\home\{username}\.config\SCP Secret Laboratory\config\<port>\config_gameplay.txt`

## <a id="Verification">Верификация</a>
Сервер должен быть проверен перед тем, как станет видимым в Обозревателе серверов.

Перед запросом верификации, убедитесь, что ваш сервер соответствует [Правилам Верифицированных Серверов](https://scpslgame.com/Verified_server_rules.pdf).

### Запрос верификации
Когда все будет готово, отправьте e-mail на **server.verification@scpslgame.com** со следующей информацией:
- Внешний IPv4 адрес сервера 95.52.195.175
- Порт, используемый сервером 7777
- IP-адрес является статическим или динамическим статическое

После отправки убедитесь, что ваш сервер будет работать до прохождения процедуры верификации. Обычно этот процесс занимает менее 72 часов.

## <a id="ServerExplorer">Обозреватель серверов</a>
> **Серверы** позволяют играть с другими игроками по сети. Серверы могут быть созданы как игроками, так и внешними хостинг-провайдерами. Оптимально серверы должны позволять находиться 20 игрокам. Хотя можно настроить и более крупные серверы, но они станут значительно "медленнее", а геймплей может стать несбалансированным.

 Обозреватель серверов отображает все проверенные сервера, отсортированные по задержке/локации, при этом официальные сервера в регионе игрока всегда будут отображаться первыми.

 В верху обозревателя серверов находятся 5 настроек фильтров. Эти настройки включают в себя:

- Все - Отображает все серверы в списке
- Избранные - Отображает все Избранные серверы
- Официальные - Отображает все Официальные серверы
- История - Отображает все серверы, на которых вы недавно играли.
- Друзья - Отображает все серверы, на которых в данный момент играют ваши друзья.

Выше списка серверов находятся несколько различных кнопок.

- Поиск сервера по его названию
- Создание временного сервера
- Переподключение к последнему серверу
- Прямое подключение к серверу по IP
- Обновление списка серверов

Параметры фильтра находятся справа от этих кнопок.<br>
Эти параметры фильтра используются для скрытия пустых, полных серверов, а также серверов с активированным белым списком.

Когда вы нажимаете на сервер, справа от списка серверов появляется информация об этом сервере.<br>
Большинство серверов имеют правила, записанные в разделе Информация, так что важно прочитать их перед тем, как присоединяться к серверу.

Обозреватель серверов также отображает важную информацию о сервере, такую как

- Официальный Сервер
- Сервер с активированным режимом - "Огонь по своим"
- Сервер, который использует плагины
- Сервер с активированным белым списком.

### <a id="Servermoderation">одерирование сервера</a>
Для модерирования сервера владельцы и персонал сервера используют Панель Администратора. Она позволяет использовать функции для модерации, такие как кик, бан и мут, а также "читерские" опции, такие как выдача предметов, активация режима бессмертия или обход ограничений.

## <a id="Exiled">EXILED - библиотека для разработки плагинов</a>
[EXILED](https://github.com/Exiled-Team/EXILED) — низкоуровневый фреймворк для серверов SCP: Secret Laboratory. Он предлагает систему событий, которую разработчики могут использовать для различных манипуляций, изменения кода игры или реализации собственных функций. Все ивенты EXILED сделаны с помощью Harmony, это означает, что для их функционирования не требуется прямого редактирования серверных сборок, что позволяет получить два уникальных преимущества:

- Во-первых, весь код фреймворка может быть свободно опубликован и распространен, что позволяет разработчикам лучше понять, как он работает, а также предложить свои предложения по дополнению или изменению его функций.
- Во-вторых, поскольку весь код, связанный с фреймворком, выполняется вне сборки сервера, такие вещи, как небольшие обновления игры, будут иметь незначительное влияние на фреймворк, если вообще будут иметь. Это делает его наиболее совместимым с будущими обновлениями игры, а также облегчает обновление, когда это нужно сделать.

### <a id="EXILEDInstallation">Установка</a>
Установка EXILED может показаться более сложной, чем установка других фреймворков, но на самом деле она довольно проста. Как упоминалось выше, большая часть EXILED не содержится в файле Assembly-CSharp.dll сервера, однако в файл Assembly-CSharp.dll необходимо внести одно изменение, которое требуется для того, чтобы EXILED действительно загружался на сервер при запуске, чистая сборка игры с уже внесенными изменениями будет поставляться с релизами.

Если вы решите использовать программу установки, она, при правильном запуске, "позаботится" об установке `Exiled.Loader`, `Exiled.Updater`, `Exiled.Permissions`, `Exiled.API` и `Exiled.Events`, а также о том, чтобы на вашем сервере был установлен правильный файл Assembly-CSharp.dll.

### Windows
#### Автоматическая установка ([подробнее](https://github.com/galaxy119/EXILED/blob/master/Exiled.Installer/README.md))
**Примечание**: Перед запуском программы установки убедитесь, что вы находитесь под пользователем, который запускает сервер, или у вас есть права администратора.

- Скачайте **`Exiled.Installer-Win.exe` [отсюда](https://github.com/galaxy119/EXILED/releases)** (нажмите на Assets -> нажмите на Installer).
- Поместите его в папку вашего сервера (если вы еще не скачали выделенный сервер)
- Дважды щелкните **`Exiled.Installer.exe`** 
- Чтобы установить и получить плагины, ознакомьтесь с разделом [Установка плагинов](#Установка-плагинов-Windows) ниже.
  **Примечание:** Если вы устанавливаете EXILED на удаленный сервер, убедитесь, что вы запустили .exe от имени того же пользователя, который запускает ваши серверы SCP:SL (или пользователя с правами администратора).

#### Установка вручную
- Скачайте **`Exiled.tar.gz` [отсюда](https://github.com/galaxy119/EXILED/releases)**.
- Распакуйте его содержимое с помощью [7Zip](https://www.7-zip.org/) или [WinRar](https://www.win-rar.com/download.html?&L=6).
- Переместите папку **`EXILED`** в **`%appdata%`** *Примечание: Эта папка должна находиться в ``C:\Users\(ВАШ_ПОЛЬЗОВАТЕЛЬ)\AppData\Roaming``, и ***НЕ*** ``C:\Users\(ВАШ_ПОЛЬЗОВАТЕЛЬ)\AppData\Roaming\SCP Secret Laboratory``, и **ЭТО ДОЛЖНО** быть в (. ...)\AppData\Roaming, а не (...)\AppData\!*.
- Переместите **``SCP Secret Laboratory``** в **`%appdata%`**.
  - Windows 10:
    Напишите `%appdata%` в Cortana / значке поиска или в строке проводника Windows.
  - Любая другая версия Windows:
    Нажмите Win + R и введите `%appdata%`.

#### Установка плагинов Windows
Вот и все, теперь EXILED должен быть установлен и активен при следующей загрузке вашего сервера. Обратите внимание, что EXILED сам по себе почти ничего не делает, поэтому обязательно получайте новые плагины с **[нашего сервера Discord](https://discord.gg/PyUkWTg)**.
- Чтобы установить плагин, просто:
  - Скачайте плагин с [*их* страницы релизов](https://i.imgur.com/u34wgPD.jpg) (**он ДОЛЖЕН быть `.dll`!**)
  - Переместите его в: ``C:\Users\(ВАШ_ПОЛЬЗОВАТЕЛЬ)\AppData\Roaming\EXILED\Plugins`` (переместите его сюда, нажав Win + R, а затем написав `%appdata%`)

### Linux
#### Автоматическая установка ([подробнее](https://github.com/galaxy119/EXILED/blob/master/Exiled.Installer/README.md))

**Примечание:** Если вы устанавливаете EXILED на удаленный сервер, убедитесь, что вы запускаете программу установки от имени того же пользователя, который запускает ваши серверы SCP:SL (или root).

- Скачайте **`Exiled.Installer-Linux` [отсюда](https://github.com/galaxy119/EXILED/releases)** (нажмите на Assets -> нажмите на Installer).
- Установите его, набрав **`./Exiled.Installer-Linux --path /путь/к/серверу`** или переместив его в папку сервера напрямую, перейдите в нее с помощью терминала (`cd`) и наберите: **`./Exiled.Installer-Linux`**.
- Если вам нужна последняя предварительная версия, просто добавьте **`--pre-releases`**. Пример: **`./Exiled.Installer-Linux /home/scp/server --pre-releases`**.
- Другой пример, если вы поместили `Exiled.Installer-Linux` в папку вашего сервера: **`/home/scp/server/Exiled.Installer-Linux --pre-releases`**
- Чтобы установить и получить плагины, ознакомьтесь с разделом [Установка плагинов](#устaновка-плагинов-Linux) ниже.

#### Установка вручную
- **Убедитесь**, что вы вошли в систему под пользователем, который запускает SCP-серверы.
- Скачайте **`Exiled.tar.gz` [отсюда](https://github.com/galaxy119/EXILED/releases)** (SSH: щелкните правой кнопкой мыши и получите ссылку `Exiled.tar.gz`, затем введите: **`wget (link_to_download)`**)
- Чтобы извлечь его в текущую папку, введите **``tar -xzvf EXILED.tar.gz``**.
- Переместите **`SCP Secret Laboratory`** папку в **``~/.config``**. *Примечание: Эта папка должна находиться в ``~/.config``, а ***НЕ В*** ``~/.config/SCP Secret Laboratory``* (SSH: **`mv SCP Secret Laboratory ~/.config/`**)
- Переместите папку **`EXILED`** в **``~/.config``**. *Примечание: Эта папка должна находиться в ``~/.config``, и ***НЕ В*** ``~/.config/SCP Secret Laboratory``* (SSH: **`mv EXILED ~/.config/`**)

#### Устaновка плагинов Linux
Вот и все, теперь EXILED будет установлен и активен при следующей загрузке вашего сервера. Обратите внимание, что EXILED сам по себе почти ничего не делает, поэтому обязательно получайте новые плагины с **[нашего сервера Discord](https://discord.gg/PyUkWTg)**.
- Чтобы установить плагин, просто:
  - Скачайте плагин с [*их* страницы релизов](https://i.imgur.com/u34wgPD.jpg) (**он ДОЛЖЕН быть `.dll`!**)
  - Переместите его в: ``~/.config/EXILED/Plugins`` (если вы используете SSH как root, то ищите нужный `.config`, который будет находиться в `/home/(SCP Server User)``)

### <a id="EXILEDConfiguration">Конфигурация</a>
EXILED сам по себе предлагает некоторые опции конфигурации.
Все они автоматически генерируются при запуске сервера и находятся в файле ``~/.config/EXILED/Configs/(ПортСервера)-config.yml`` (``%AppData%\EXILED\Configs\(ПортСервера)-config.yml`` на Windows).

Конфигурации плагинов ***НЕ*** будут находиться в файле ``config_gameplay.txt``, вместо этого они устанавливаются в файле ``~/.config/EXILED/Configs/(ПортСервера)-config.yml`` (``%AppData%\EXILED\(ПортСервера)-config.yml`` на Windows).
Однако некоторые плагины могут получать свои настройки конфигурации из других мест самостоятельно, это просто место по умолчанию для них в EXILED'е, поэтому при возникновении проблем обратитесь к отдельному плагину.

### <a id="Fordevelopers">Для разработчиков</a>
Если вы хотите создать плагин для EXILED, это сделать довольно просто. Если вам нужны дополнительные руководства, посетите нашу страницу «[Начало работы](https://github.com/Exiled-Team/EXILED/blob/master/GettingStarted.md)».
> Более полные и постоянно обновляемые руководства можно найти на веб-сайте [EXILED](https://exiled-team.github.io/EXILED/articles/install.html).

Но обязательно соблюдайте следующие правила при публикации своих плагинов:
- Ваш плагин должен содержать класс, который наследуется от ``Exiled.API.Features.Plugin<>``, в противном случае EXILED не будет загружать ваш плагин при запуске сервера.
 - Когда плагин загружается, код внутри метода `OnEnabled()` вышеупомянутого класса запускается немедленно, он не ждет загрузки других плагинов. Он не ждет завершения процесса запуска сервера. **Он ничего не ждет.** При настройке метода `OnEnabled()` убедитесь, что вы не получаете доступ к вещам, которые еще не инициализированы сервером, например, `ServerConsole.Port`, или `PlayerManager.localPlayer`.
 - Если вам нужно получить доступ к вещам на ранней стадии, которые не инициализируются до загрузки вашего плагина, рекомендуется просто дождаться события `WaitingForPlayers`, чтобы сделать это. Если вам по какой-то причине нужно сделать что-то раньше, оберните код в цикле `while(!x)`, который проверяет, что переменная/объект, который вам больше не должен быть нулевым, прежде чем продолжить.
 - EXILED поддерживает `динамическую перезагрузку` сборок плагинов во время выполнения. Это означает, что если вам нужно обновить плагин, это можно сделать без перезагрузки сервера, однако, если вы обновляете плагин в середине выполнения, плагин необходимо правильно настроить для его поддержки, иначе у вас будет очень плохое время. Обратитесь к разделу «Динамические обновления» для получения дополнительной информации и рекомендаций, которым необходимо следовать.
 - В EXILED нет событий OnUpdate, OnFixedUpdate или OnLateUpdate **NO**. Если по какой-то причине вам нужно часто запускать код, вы можете использовать сопрограмму MEC, которая ожидает один кадр, 0.01f, или вместо этого использует слой синхронизации, например Timing.FixedUpdate.

 ### Отключение патчей событий EXILED
 **Эта функция в настоящее время больше не реализована.**

 ### MEC Coroutines
 Если вы не знакомы с MEC, это будет очень краткое и простое руководство для начала. Сопрограммы MEC — это, по сути, синхронизированные методы, которые поддерживают периоды ожидания перед продолжением выполнения без прерывания/переключения основного игрового потока. Сопрограммы MEC безопасно использовать с Unity, в отличие от традиционной многопоточности. **НЕ пытайтесь создавать новые потоки для взаимодействия с Unity, они ПРИВЕДЯТ к сбою сервера**.

 Чтобы использовать MEC, вам необходимо будет сослаться на файл `Assembly-CSharp-firstpass.dll` из файлов сервера и включить `using MEC;`. Пример вызова простой сопрограммы, которая повторяется с задержкой между каждым циклом:
```cs
using MEC;
using Exiled.API.Features;

public void SomeMethod()
{
    Timing.RunCoroutine(MyCoroutine());
}

public IEnumerator<float> MyCoroutine()
{
    for (;;) //повторять следующее бесконечно
    {
        Log.Info("Hey I'm a infinite loop!"); //Вызовите Log.Info, чтобы вывести строку в журналы игровой консоли/сервера.
        yield return Timing.WaitForSeconds(5f); //Сообщает сопрограмме подождать 5 секунд, прежде чем продолжить, поскольку это конец цикла, это эффективно останавливает повторение цикла на 5 секунд.
    }
}
```
**Настоятельно рекомендуется** погуглить или спросить в Discord, если вы не знакомы с MEC и хотите узнать больше, получить совет или нуждаетесь в помощи. На вопросы, какими бы «глупыми» они ни были, всегда будут даны максимально полезные и ясные ответы, чтобы разработчики плагинов могли преуспеть. Чем лучше код, тем лучше для всех.

### Динамические обновления
EXILED как фреймворк поддерживает динамическую перезагрузку сборок плагинов без перезагрузки сервера. Например, если вы запускаете сервер только с `Exiled.Events` в качестве единственного плагина и хотите добавить новый, вам не нужно перезагружать сервер для выполнения этой задачи. Вы можете просто использовать команду `reload plguins` RemoteAdmin/ServerConsole, чтобы перезагрузить все плагины EXILED, включая новые, которые не были загружены ранее.

Это также означает, что вы можете обновлять плагины без необходимости полной перезагрузки сервера. Однако есть несколько рекомендаций, которым должен следовать разработчик плагина, чтобы это было достигнуто должным образом:

**Для хостов**
- Если вы обновляете плагин, убедитесь, что имя его сборки не совпадает с именем текущей версии, которую вы установили (если таковая имеется). Чтобы это работало, плагин должен быть создан разработчиком с учетом динамических обновлений, простое переименование файла не поможет.
- Если плагин поддерживает динамические обновления, убедитесь, что, когда вы помещаете более новую версию плагина в папку «Плагины», вы также удаляете старую версию из папки, прежде чем перезагрузить EXILED, несоблюдение этого приведет ко многим плохим последствиям. вещи.
- За любые проблемы, возникающие в результате динамического обновления плагина, ответственность несете исключительно вы и разработчик соответствующего плагина. Хотя EXILED полностью поддерживает и поощряет динамические обновления, единственный случай, когда оно может выйти из строя или пойти не так, — это если хост сервера или разработчик плагина сделали что-то не так. Трижды проверьте, что обе стороны все сделали правильно, прежде чем сообщать разработчикам EXILED об ошибке, касающейся динамических обновлений.

**Для разработчиков**
- Плагины, которые хотят поддерживать динамическое обновление, должны обязательно отказаться от подписки на все события, к которым они подключены, когда они отключены или перезагружены.
- Плагины, имеющие собственные патчи Harmony, должны использовать какую-то изменяющуюся переменную в имени экземпляра Harmony и должны использовать `UnPatchAll()` в своем экземпляре гармонии, когда плагин отключен или перезагружен.
- Любые сопрограммы, запущенные плагином в `OnEnabled()`, также должны быть уничтожены, когда плагин отключен или перезагружен.

Все это может быть достигнуто с помощью методов `OnReloaded()` или `OnDisabled()` в классе плагина. Когда EXILED перезагружает плагины, он вызывает `OnDisabled()`, затем `OnReloaded()`, затем загружает новые сборки и затем выполняет `OnEnabled()`.

Заметьте, я сказал новые сборки. Если вы замените сборку другой с тем же именем, она **НЕ будет** обновлена. Это связано с GAC (глобальным кэшем сборок): если вы попытаетесь «загрузить» сборку, которая уже находится в кеше, вместо этого всегда будет использоваться кэшированная сборка. По этой причине, если ваш плагин будет поддерживать динамические обновления, вы должны собрать каждую версию с другим именем сборки в параметрах сборки (переименование файла не будет работать). Кроме того, поскольку старая сборка не «уничтожается», когда она больше не нужна, если вам не удастся отписаться от событий, удалить исправления экземпляра гармонии, уничтожить сопрограммы и т. д., этот код продолжит работать так же, как и код новой версии. Это очень-очень плохая идея.

Таким образом, плагины, поддерживающие динамические обновления, **ДОЛЖНЫ** следовать этим рекомендациям, иначе они будут удалены с сервера Discord из-за потенциального риска для хостов серверов.

Но не каждый плагин должен поддерживать динамические обновления. Если вы не собираетесь поддерживать динамические обновления, это совершенно нормально, просто не меняйте имя сборки вашего плагина при создании новой версии, и вам не придется беспокоиться ни о чем из этого, просто убедитесь, что хосты серверов знают об этом. им потребуется полностью перезагрузить свои серверы, чтобы обновить ваш плагин.