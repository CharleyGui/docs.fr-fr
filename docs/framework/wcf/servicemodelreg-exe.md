---
title: Outil d'inscription ServiceModel (ServiceModelReg.exe)
description: Utilisez cet outil en ligne de commande pour gérer l’inscription des composants WCF et WF sur un ordinateur unique si vous rencontrez des problèmes avec l’activation du service.
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 347b1b8071abe7d8eb7e16ffd879c1fdb9825bc7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245893"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Outil d'inscription ServiceModel (ServiceModelReg.exe)
Cet outil en ligne de commande permet de gérer l'inscription des composants WCF et WF sur un ordinateur unique. Dans des circonstances normales vous n'avez pas à utiliser cet outil, car les composants WCF et WF sont configurés lors de l'installation. Mais si vous rencontrez des problèmes avec l'activation de service, vous pouvez essayer d'inscrire les composants à l'aide de cet outil.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Notes  
 Cet outil se trouve à l'emplacement suivant :  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
> Lorsque l’outil d’inscription ServiceModel est exécuté sur Windows Vista, la boîte de dialogue **fonctionnalités de Windows** peut ne pas refléter le fait que l’option d' **Activation Windows Communication Foundation http** sous **Microsoft .NET Framework 3,0** est activée. Vous pouvez accéder à la boîte de dialogue **fonctionnalités de Windows** en cliquant sur **Démarrer**, puis sur **exécuter** et en tapant **OptionalFeatures**.  
  
 Les tableaux suivants décrivent les options qui peuvent être utilisées avec ServiceModelReg.exe.  
  
|Option|Description|  
|------------|-----------------|  
|`-ia`|Installe les composants WCF et WF.|  
|`-ua`|Désinstalle les composants WCF et WF.|  
|`-r`|Répare les composants WCF et WF.|  
|`-i`|Installe les composants WCF et WF spécifiés avec –c.|  
|`-u`|Désinstalle les composants WCF et WF spécifiés avec –c.|  
|`-c`|Installe ou désinstalle un composant :<br /><br /> -httpnamespace – réservation d’espace de noms HTTP<br />-tcpportsharing – service de partage de ports TCP<br />-tcpactivation – service d’activation TCP (non pris en charge sur .NET 4 Client Profile)<br />-namedpipeactivation – service d’activation de canal nommé (non pris en charge sur .NET 4 Client Profile<br />-MsmqActivation – service d’activation MSMQ (non pris en charge sur .NET 4 Client Profile<br />-ETW – manifestes de suivi d’événements ETW (Windows Vista ou version ultérieure)|  
|`-q`|Mode silencieux (enregistrement des erreurs d'affichage uniquement)|  
|`-v`|Mode documenté.|  
|`-nologo`|Supprime le message de copyright et de bannière.|  
|`-?`|Affiche le texte de l'aide.|  
  
## <a name="fixing-the-fileloadexception-error"></a>Résolution de l'erreur FileLoadException  
 Si vous avez installé des versions précédentes de WCF sur votre ordinateur, vous risquez d’obtenir une `FileLoadFoundException` erreur quand vous exécutez l’outil ServiceModelReg pour inscrire une nouvelle installation. Cela peut se produire même si vous avez supprimé manuellement les fichiers de la précédente installation, mais que vous avez conservé les paramètres machine.config.  
  
 Le message d'erreur est semblable au message suivant.  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Ce message d’erreur indique que l’assembly de la version 2.0.0.0 de System.ServiceModel a été installé par une mise en production antérieure de CTP (Customer Technology Preview). La version actuelle de l’assembly System.ServiceModel est la version 3.0.0.0. Par conséquent, ce problème se produit lorsque vous souhaitez installer la version officielle de WCF sur un ordinateur sur lequel une version CTP préliminaire de WCF a été installée, mais qui n’a pas été complètement désinstallée.  
  
 ServiceModelReg.exe ne peut pas nettoyer les entrées de versions antérieures ; il ne peut pas non plus enregistrer les entrées de la nouvelle version. La seule solution consiste à modifier manuellement machine.config. Vous pouvez localiser ce fichier à l’emplacement suivant.  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 Si vous exécutez WCF sur un ordinateur 64 bits, vous devez également modifier le même fichier à cet emplacement.  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 Recherchez dans ce fichier tous les nœuds XML qui font référence à « System. ServiceModel, version = 2.0.0.0 », supprimez-les et tous les nœuds enfants. Enregistrez le fichier et réexécutez ServiceModelReg.exe afin de résoudre ce problème.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants indiquent comment utiliser les options les plus courantes de l'outil ServiceModelReg.exe.  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
