# Kirill Guzarevich
# *Junior Frontend Developer*
# My contacts
* Email: guzarevichkirill@gmail.com
* Telegram: @xxxx_cs
# **About myself**
My name is Kirill, I am 19 yers old and study to be a marketing specialist at the university. But I feel that it isn't what I want, so that I decide to learn coding. I should write more about myself, however idk who l really am. My biggest trouble is that I'm not disciplined and so lazy. To be honest it is my second try to start this course. So l wanna just overcome myself and start to dive into IT.
# Skills 
* Basics C++
* Basics Git
# Code example
~~~C++
#include <iostream>
#include <winsock2.h>
#include <WS2tcpip.h>
#include <string>

#pragma comment (lib, "ws2_32.lib")

using namespace std;

int main()
{
  // Запустить Winsock

  WSADATA data;
  int wsOK = WSAStartup(MAKEWORD(2, 2), &data);

  if (wsOK != 0)
  {
    cout << "Can't startup Winsock " << wsOK << endl;
    return 1;
  }

  // установить адрес сервера
  
  sockaddr_in server;
  server.sin_family = AF_INET;
  server.sin_port = htons(54000);
  inet_pton(AF_INET, "127.0.0.1", &server.sin_addr);
  int LengthServer = sizeof(server);
  // создать сокет
  
  SOCKET s = socket(AF_INET, SOCK_DGRAM, 0);

  // отправить сообщение
  string str;
  cout << "Enter the string: ";
  getline(cin,str);
  int sendOK = sendto(s, str.c_str(), str.size()+1, 0, (sockaddr*)&server, sizeof(server));
   
  if (sendOK == SOCKET_ERROR)
  {
    cout << "Can't send to server " << endl; 
  }

  // получение результата от сервера
  char buf[1024];
  int bytesReceived = recvfrom(s, buf, 1024, 0, (sockaddr*)&server, &LengthServer);

  if (bytesReceived == SOCKET_ERROR)
  {
    cout << "Can't receive the message from server " << WSAGetLastError() << endl;
    closesocket(s);
    WSACleanup();
    return 1;
  }
  cout << buf << endl;
  closesocket(s);
  WSACleanup();

  return 0;
}
~~~
# Languages
* Russian native
* English B1