---
id: 102
title: 'C Socket Programlama - Client / Server Uygulaması'
date: 2013-07-18T03:05:30+00:00
author: Hakan
layout: post
permalink: /c-socket-programlama-client-server-uygulamasi/
categories:
  - C Programlama
tags:
  - c ile
  - c programlama
  - c programlama ile
  - c socket programlama
  - c soket programlama
  - client server
  - network programlama
  - örneği
  - örnek uygulama
  - socket
  - socket nedir
  - tcp/ip
---
Bu yazımızda C programlama dili ile Linux üzerinde, örnek olması açısından iki uygulamanın haberleşmesini sağlayacağız. Socket, basitçe iki prosesin TCP/IP protokolü üzerinden haberleşmesi için açılan kapı olarak tanımlayabiliriz. Network üzerinde veri aktarımı için öncelikle socket() metoduyla bir socket açmamız, bu sockete de bind() metodu ile bir port numarası atamalıyız. Socketler listen() çağrısıyla bağlantıları dinler, accept() metoduyla bağlantıları kabul eder. Socketler connect() çağrısı ile belirtilen adrese bağlantı sağlar. Socketler send() metoduyla veri gönderir, recv() metoduyla veri alır. 

Şimdi basit olarak clientın servera bağlanıp bir mesaj aldığını kurgulayalım. Server için;
  
- socket() ile bir socket oluşturulacak
  
- bind() ile sockete bir port bağlanacak
  
- listen() ile bağlanan port dinlenecek
  
- accept() ile varsa bağlantı kabul edilecek
  
- send() ile kabul edilen bağlantıya veri gönderilecek
  
- close() ile kabul edilen bağlantı kapatılacak.

Client için;
  
- socket() ile bir socket oluşturulacak
  
- connect() ile belirtilen adrese bağlantı isteği gönderecek ve bağlanacak
  
- recv() ile bağlandığı adresten veri alacak.


Örnek uygulamada, client server&#8217;a bağlandığı zaman server client&#8217;a &#8220;Hello Client!&#8221; mesajı gönderecek ve client bu mesajı alacaktır.

Server.c ve client.c dosyaları derlendikten sonra ilgili dizinde ./server komutu ile server uygulaması başlatılır, ./client 127.0.0.1 komutu ile client uygulaması başlatılır. Örnek uygulamada port numarası olarak 7841 verdik. Tabi bu komutlar client ve server uygulamalarının aynı bilgisayar üzerinde koştuğu durumda geçerli. 

Server.c

{% highlight php %} 
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <sys/types.h>

int main(int argc, char *argv[])
{
    int listenfd = 0, connfd = 0;
    struct sockaddr_in serv_addr; 

    char sendBuff[1025];

    listenfd = socket(AF_INET, SOCK_STREAM, 0);
    memset(&#038;serv_addr, '0', sizeof(serv_addr));
    memset(sendBuff, '0', sizeof(sendBuff)); 

    serv_addr.sin_family = AF_INET;
    serv_addr.sin_addr.s_addr = htonl(INADDR_ANY);
    serv_addr.sin_port = htons(7841); 

    bind(listenfd, (struct sockaddr*)&#038;serv_addr, sizeof(serv_addr)); 

    listen(listenfd, 10); 

    while(1)
    {
        connfd = accept(listenfd, (struct sockaddr*)NULL, NULL); 
		char data[]="Hello Client! \n";
		send(connfd, data, strlen(data)+1, 0);
		
        close(connfd);
        sleep(1);
     }
}
{% endhighlight %} 
    

Client.c

{% highlight php %}    
#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <netdb.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <arpa/inet.h> 

int main(int argc, char *argv[])
{
    int sockfd = 0, n = 0;
    char recvBuff[1024];
    struct sockaddr_in serv_addr; 

    if(argc != 2)
    {
        printf("\n Usage: %s <ip of server> \n",argv[0]);
        return 1;
    } 

    memset(recvBuff, '0',sizeof(recvBuff));
    if((sockfd = socket(AF_INET, SOCK_STREAM, 0)) < 0)
    {
        printf("\n Error : Could not create socket \n");
        return 1;
    } 

    memset(&#038;serv_addr, '0', sizeof(serv_addr)); 

    serv_addr.sin_family = AF_INET;
    serv_addr.sin_port = htons(7841); 

    if(inet_pton(AF_INET, argv[1], &#038;serv_addr.sin_addr)<=0)
    {
        printf("\n inet_pton error occured\n");
        return 1;
    } 

    if( connect(sockfd, (struct sockaddr *)&#038;serv_addr, sizeof(serv_addr)) < 0)
    {
       printf("\n Error : Connect Failed \n");
       return 1;
    } 

    while ( (n = read(sockfd, recvBuff, sizeof(recvBuff)-1)) > 0)
    {
        recvBuff[n] = 0;
        if(fputs(recvBuff, stdout) == EOF)
        {
            printf("\n Error : Fputs error\n");
        }
    } 

    if(n < 0)
    {
        printf("\n Read error \n");
    } 

    return 0;
}
{% endhighlight %}