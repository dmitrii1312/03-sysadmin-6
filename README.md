## 1 В ответе укажите полученный HTTP код, что он означает?
	
	GET /questions HTTP/1.0
	HOST: stackoverflow.com
	
	HTTP/1.1 301 Moved Permanently

Код означает, что содержимое сайта перемещено, и браузеру нужно перейти по другому адресу.

## 2 Повторите задание 1 в браузере, используя консоль разработчика F12

### 2.4 укажите в ответе полученный HTTP код

	Status Code: 307 Internal Redirect
	
### 2.5 проверьте время загрузки страницы, какой запрос обрабатывался дольше всего?

	Request URL: https://stackoverflow.com/
	Request Method: GET
	Status Code: 200 
	Remote Address: 151.101.193.69:443
	426 ms
	
### 2.6 приложите скриншот консоли браузера в ответ.

![image](https://user-images.githubusercontent.com/93075740/145064270-c1e1375a-14e1-47bb-a023-b270e89f8f30.png)

## 3 Какой IP адрес у вас в интернете?

	188.143.142.181
	
## 4 Какому провайдеру принадлежит ваш IP адрес? Какой автономной системе AS? Воспользуйтесь утилитой whois

	netname:        PIN-NET
	origin:         as44050
	
## 5 Через какие сети проходит пакет, отправленный с вашего компьютера на адрес 8.8.8.8? Через какие AS? Воспользуйтесь утилитой traceroute

	$ traceroute -An 8.8.8.8
	traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
	 1  192.168.22.199 [*]  3.556 ms  3.483 ms  3.403 ms
	 2  188.143.178.1 [as44050]  3.334 ms  3.356 ms  3.323 ms
	 3  * * *
	 4  95.215.3.17 [as44050]  3.110 ms 95.215.3.25 [as44050]  3.075 ms 95.215.3.17 [as44050]  4.221 ms
	 5  74.125.244.133 [AS15169]  3.647 ms 74.125.244.181 [AS15169]  8.293 ms  6.627 ms
	 6  * 72.14.232.84 [AS15169]  3.271 ms 142.251.61.221 [AS15169]  8.548 ms
	 7  142.251.61.219 [AS15169]  8.419 ms 216.239.54.201 [AS15169]  9.842 ms 142.251.61.219 [AS15169]  8.307 ms
	 8  216.239.49.115 [AS15169]  9.452 ms * 172.253.64.51 [AS15169]  9.261 ms
	 9  * * *
	10  * * *
	11  * * *
	12  * * *
	13  * * *
	14  * * *
	15  * * *
	16  * * *
	17  * * *
	18  * 8.8.8.8 [AS15169]  6.711 ms  6.237 ms
	
Через AS44050 и AS15169

## 6 Повторите задание 5 в утилите mtr. На каком участке наибольшая задержка - delay?

	                             My traceroute  [v0.85]
	test-hystax (0.0.0.0)                                  Tue Dec  7 19:22:33 2021
	Keys:  Help   Display mode   Restart statistics   Order of fields   quit
	                                       Packets               Pings
	 Host                                Loss%   Snt   Last   Avg  Best  Wrst StDev
	 1. 192.168.22.199                    0.0%    26    1.0   1.1   0.3   2.5   0.3
	 2. 188.143.178.1                     0.0%    25    0.9   3.9   0.9  26.9   6.0
	 3. ???
	 4. 95.215.3.17                       0.0%    25    8.2   2.6   1.2   8.9   1.8
	 5. 74.125.244.133                    0.0%    25   13.2   5.3   1.3  21.4   5.0
	 6. 142.251.61.221                    0.0%    25    6.5   6.5   5.4  13.2   1.4
	 7. 172.253.79.237                    0.0%    25    5.4   5.4   4.5   6.8   0.2
	 8. ???

В среднем самые большие задержки на участке 6.

## 7 Какие DNS сервера отвечают за доменное имя dns.google? Какие A записи? воспользуйтесь утилитой dig

	dig NS dns.google.
	
	;; ANSWER SECTION:
	dns.google.		21600	IN	NS	ns3.zdns.google.
	dns.google.		21600	IN	NS	ns4.zdns.google.
	dns.google.		21600	IN	NS	ns1.zdns.google.
	dns.google.		21600	IN	NS	ns2.zdns.google.
	
	;; ADDITIONAL SECTION:
	ns3.zdns.google.	86037	IN	A	216.239.36.114
	ns3.zdns.google.	86037	IN	AAAA	2001:4860:4802:36::72
	ns4.zdns.google.	86037	IN	A	216.239.38.114
	ns4.zdns.google.	86037	IN	AAAA	2001:4860:4802:38::72
	ns1.zdns.google.	86037	IN	A	216.239.32.114
	ns1.zdns.google.	86037	IN	AAAA	2001:4860:4802:32::72
	ns2.zdns.google.	86037	IN	A	216.239.34.114
	ns2.zdns.google.	86037	IN	AAAA	2001:4860:4802:34::72


	dig 8.8.4.4
	dns.google.		398	IN	A	8.8.4.4
	
	dig 8.8.8.8
	dns.google.		398	IN	A	8.8.8.8
	
## 8 Проверьте PTR записи для IP адресов из задания 7. Какое доменное имя привязано к IP? воспользуйтесь утилитой dig

	dig -x 8.8.4.4
	4.4.8.8.in-addr.arpa.	10773	IN	PTR	dns.google.
	
	dig -x 8.8.8.8
	8.8.8.8.in-addr.arpa.	43472	IN	PTR	dns.google.

