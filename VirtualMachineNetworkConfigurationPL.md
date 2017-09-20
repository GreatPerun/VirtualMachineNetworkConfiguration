#Konfiguracja sieci na maszynie wirtualnej

###Rodzaje interfejsów z opisami

- Not Attached – interfejs sieciowy jest dostępny w systemie goszczonym, jednak będzie on wykazywał brak podłączonego kabla sieciowego.
- NAT – domyślne ustawienie VirtualBox, które powoduje, że system goszczony zachowuje się jakby był podłączony do routera, który udostępnia nam połączenie sieciowe. W zupełności wystarcza to do pracy maszyny w internecie, jednak posiada swoje ograniczenia w perspektywie połączeń sieciowych z wirtualną maszyną ze środowisk fizycznych
- Bridged Networking – powoduje zmostkowanie wirtualnego interfejsu z fizyczną kartą sieciową, jaką wykorzystujemy do połączenia z siecią. Pozwala to na bezpośredni przepływ danych pomiędzy systemem goszczonym a środowiskiem fizycznym. Uaktywnienie tej opcji, pozwala nam na wybór karty sieciowej z której chcemy skorzystać.
- Internal Networking – opcja ta powoduje uruchomienie wirtualnej sieci, w której znajdują się maszyny mając bezpośrednie połączenie sieciowe ze sobą. Jest to zdecydowanie najpopularniejsza forma połączenia, która pozwala na tworzenie zamkniętych środowisk laboratoryjnych służących testom usług i wzajemnej współpracy systemów. Po wybraniu opcji możemy dowolnie nazwać naszą wewnętrzną sieć wirtualną.
- Host-only Networking – jest to konfiguracja podobna do Internal Network jednak powoduje ona, że w wirtualnej sieci znajduje się również nasza maszyna fizyczna. Co ważne, do tego połączenia nie jest wykorzystywany nasz fizyczny interfejs sieciowy. VirtualBox, tworzy na maszynie fizycznej dodatkowy kontroler sieci, który to właśnie odpowiada za zachowanie komunikacji pomiędzy środowiskiem wirtualnym i fizycznym
- Generic Networking – jest to niezwykle rzadko używana opcja, która pozwala na użycie dowolnego sterownika, i dystrybuuje go do maszyny wirtualnej. W 99% jest to nie użyteczna opcja dla użytkowników.


###Działające rozwiązania:

1. Bridged Networking

Nowe IP zostało nadane samo, dla czego, nie mam pojęcia :D

    source /etc/network/interfaces.d/*

    auto lo
    iface lo inet loopback

    auto enp0s3
    iface enp0s3 inet dhcp
