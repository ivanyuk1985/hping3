## Базове використання інструменту hping3:  
**-v** – version відображає поточну версію hping3  
**-c** – лічильник пакетів  
**-i** – період тайм-ауту (uX для X мікросекунд, наприклад -i u1000(10 пакетов в секунду),-i u1000 (100 пакетов в секунду))        
       –Flood відправляє пакети максимально швидко, не відображає відповіді.  
**-n** - числовий вивід з числами  
**-q** - команда без відображення повідомлень на екран  
**-I** - імя інтерфейсу, ящо нічого не визначено, за замовчуванням використовується вказаний вище інтерфейз шлюзу.  
**-V** - детальний режим налагодження  
**–Bip** beep для для кожного полученого пакету, який задовільняє

## Режими hping3:

Режим по умолчанию - TCP
-0 - режим RAW rawip IP
-1 –icmp режим ICMP
-2 –udp режим UDP
-8 - режим сканування
-9 - режим прослуховування

 ## IP:

**-a** –spoof IP-адрес - підробити ip-адресу джерела.  
**–Rand**-dest Випадкова IP-адреса призначення.  
**-t** –ttl ttl (за замовчуванням 64) час життя пакету.  
**-N** –id id (за замовчуванням випадковий).  
**-r** –rel релятивізувати поле id (для оцінки трафіку хосту).. 
**-f** –frag розділяє пакети на декілька фрагментів, може проходити по слабким ACL.  
**-x** - більше фрагментів.  
**-y** –dontfrag не фрагментує пакети.  
**-g** –fragoff встановити зміщення фрагменту  
**-m** –mtu визначає віртуальний MTU, це значить, що фрагмент пакету більше, ніж MTU.  
**-o** –tos тип сервісу (замовчуванню 0x00), спробуйте виконати –tos help.    
**-G** –rroute включити параметр RECORD_ROUTE і і відобразити буфер шляху.  
**-H** –ippro, щоб встановити протокол IP, тільки для режиму RAW IP.  

## ICMP:

**-C** –icmptype Тип ICMP (за замовчуванням, ехо-запит ICMP)  
**-K** –icmpcode Код ICMP (за замовчуванням 0)  
**–Force-icmp** надсилає всі типи ICMP (за замовчуванням надсилає тільки підтримувані типи)  
**–Icmp-gw** встановлює адресу шлюзу за замовчуванням для перенаправлення ICMP (за замовчуванням 0.0.0.0)  
**–Icmp-ts** псевдонім для –icmp –icmptype 13 (тимчасова мітка ICMP)  
**–Icmp-addr** псевдонім для –icmp –icmptype 17 (адреса маски підмережі ICMP)  
**–Icmp-help** відображає довідку по по іншим параметрам icmp.  

## TCP / UDP

**-s** –baseport базовий порт джерела, за замовчуванням - випадковий  
**-p** –destport [+] [+] положення призначення (за замовчуванням 0)  
**-k** –keep зберегти порт джерела  
**-w** - розмір вікна Win, за замовчуванням 64  
**-O** –tcpoff встановити для зміщення даних TCP значення false (вместо tcphdrlen / 4)  
**-Q** –seqnum відображати тільки порядковий номер  
**-b** –badcksum (намагатись) надсилати пакети з підробленою контрольною сумою IP, багато систем виправлять цю контрольну суму при надсиланні пакету, тому ви отримаєте неправильну контрольну суму на рівні UDP / TCP.  
**-M** –setseq встановлює порядковий номер TCP  
**-L** –setack встановити TCP ack  
**-F** - end встановлює прапорець КІНЕЦЬ  
**-S** –syn встановити прапорець SYN  
**-R** –rst встановлює прапорець RST  
**-P** –push встановлює прапорець PUSH  
**-A** –ack встановлює прапорець ACK  
**-U** –urg встановлює прапорець URG  
**-X** –xmas встановити невикористовуваний прапорець X (0x40) 
**-Y** –ymas встановлює невикористовуваний прапорець Y (0x80) 
**–Tcpexitcode** використовує останні tcp-> th_flags в якості коду виходу.  
**–Tcp-mss** включає опцію TCP MSS з заданим значенням  
**–Tcp-timestamp** позволяет опции отметки времени TCP предполагать доступность.  

## Загальні для всіх варіанти:

**d** - розмір даних, за замовчуванням 0.  
**-E** - дані з файлу.  
**-e** –sign додати підпис  
**-j** –дамп пакетів в шістнадцятковому форматі  
**-J** –друковати пусты друкованы символи  
**-B** –safe активувати безпечний протокол  
**-u** –end повідомляє вам коли файл досягнув кінця  
**-T** –traceroute режим traceroute (мається на увазі –bind и –ttl 1)  
**–Tr-stop** Вийти, коли перший пакет не-ICMP пакет отриманий  traceroute.  
**–Tr-keep-ttl** Сохранять фиксированный TTL источника, полезно для мониторинга одиночного перехода  
**–Tr-no-rtt** Не вычислять и отображать информацию RTT в режиме traceroute.  
Описание пакета ARS (нового и нестабильного)  
**–Apd**-send Отправлять пакеты, описанные с помощью APD  

## Приклади:  

## Простий тест ping:  
hping3 -1 www.google.es  

## Намалювати шлях підключення:  
hping3 -S www.google.es –p 80  

## Підписувати пакети за допомогою налаштовуваного текстового файлу:  
hping3 redeszone.net -d 50 -E firmaredeszone.txt  

Введені параметри означають:  

-d: довжина повідомлення, яке ми збираємось ввести, в даному випадку 50.  
-E: файл, з якого ми візьмемо підпис повідомлення, яке ми хочемо ввести в пакети  

## Згенерувати декілька запитів для тестування захисту від DoS и DDoS:  

hping3 --rand-source 192.168.1.1  

Також ми можемо додати параметр –flood, щоб пакети відправлялись великими партіями в реальному часі. Таким чином, ми зможемо перевірити, з одною сторони , чи працює наш брандмауер, а з другої - наскільки добре наша система реагує на загрозу DDoS-атаки:  

hping3 --rand-source --flood 192.168.1.1  

## Сканування ACK на порту 80:  

hping3 -A 10.0.0.25 -p 80  

## Сканування UDP на порту 80:    

hping3 -2 10.0.0.25 -p 80  

##  Збір початкового номеру послідовності:  

hping3 192.168.1.103 -Q -p 139 -s  

## Брандмауери і мітки часу:  

hping3 -S 72.14.207.99 -p 80 --tcp-timestamp  

SYN-сканирование на порту 50-60  

## Сканування FIN, PUSH и URG на порту 80:   

hping3 -F -P -U 10.0.0.25 -p 80  

## Сканування всієї підмережі на наявність живого хосту:  

hping3 -1 10.0.1.x --rand-dest -I eth0  

## Переловлення всього трафіку якмй містить HTTP:  

hping3 -9 HTTP -I eth0  

## SYN флуд:  

hping3 -S 192.168.1.1 -a 192.168.1.254 -p 22 --flood  

## Визначена кількість пінгів:  

hping3 -c 3 10.10.10.10  

## Підробити адрес джерела:  

hping3 -S [IP-адрес призначення] -a [підроблена IP-адреса] або hping3 -S [IP-адрес призначенн] --spoof [підроблена IP-адреса]  

