---
tags: [sistemi_informativi]
---
Una CPU virtuale è un componente software che, agli occhi dell’utilizzatore, fornisce capacità di elaborazione come una CPU normale con però i vantaggi che arrivano dal disaccoppiamento delle delle risorse:
	• disaccoppiamento ulteriore tra software e risorse fisiche
	• frazionamento delle risorse fisiche in più virtuali
	• condivisione delle risorse fisiche tra quelle virtuali

Questi applicativi sono detti macchine virtuali #VM, la corrispondenza tra le risorse virtuali e fisiche è gestita dall' #hypervisor che può essere installato bare metal o sopra ad un OS. #XEN #VMWare #VirtualBox #KVM

![[VM.png]]

Un ultimo vantaggio delle #VM è la capacità di migrazione da una macchina fisica ad un'altra, normalmente si fa a freddo, ma si possono anche fare a caldo