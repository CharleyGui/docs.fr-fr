---
title: Outil d'inscription ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183108"
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
> Lorsque l’outil d’enregistrement De ServiceModel est exécuté sur Windows Vista, le dialogue **Windows Features** peut ne pas refléter que l’option **d’activation HTTP de la Fondation De communication Windows** dans le cadre de Microsoft **.NET Framework 3.0** est activée. Le dialogue **Windows Features** peut être consulté en cliquant sur **Démarrer,** puis cliquez **sur Run,** puis en tapant **OptionalFeatures**.  
  
 Les tableaux suivants décrivent les options qui peuvent être utilisées avec ServiceModelReg.exe.  
  
|Option|Description|  
|------------|-----------------|  
|`-ia`|Installe les composants WCF et WF.|  
|`-ua`|Désinstalle les composants WCF et WF.|  
|`-r`|Répare les composants WCF et WF.|  
|`-i`|Installe les composants WCF et WF spécifiés avec –c.|  
|`-u`|Désinstalle les composants WCF et WF spécifiés avec –c.|  
|`-c`|Installe ou désinstalle un composant :<br /><br /> - httpnamespace - HTTP Namespace Reservation<br />- tcpportsharing - Service de partage de ports TCP<br />- tcpactivation - Service d’activation TCP (non pris en service sur .NET 4 Profil client)<br />- nommépipeactivation - Service d’activation de tuyaux nommés (non pris en service sur .NET 4 Profil client<br />- msmqactivation - Service d’activation MSMQ (non pris en service sur .NET 4 Profil client<br />- etw - ETW event tracing manifestes (Windows Vista ou plus tard)|  
|`-q`|Mode silencieux (enregistrement des erreurs d'affichage uniquement)|  
|`-v`|Mode documenté.|  
|`-nologo`|Supprime le message de copyright et de bannière.|  
|`-?`|Affiche le texte de l'aide.|  
  
## <a name="fixing-the-fileloadexception-error"></a>Résolution de l'erreur FileLoadException  
 Si vous avez installé des versions précédentes de `FileLoadFoundException` WCF sur votre machine, vous pouvez obtenir une erreur lorsque vous exécutez l’outil ServiceModelReg pour enregistrer une nouvelle installation. Cela peut se produire même si vous avez supprimé manuellement les fichiers de la précédente installation, mais que vous avez conservé les paramètres machine.config.  
  
 Le message d'erreur est semblable au message suivant.  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Ce message d’erreur indique que l’assembly de la version 2.0.0.0 de System.ServiceModel a été installé par une mise en production antérieure de CTP (Customer Technology Preview). La version actuelle de l’assembly System.ServiceModel est la version 3.0.0.0. Par conséquent, ce problème est rencontré lorsque vous voulez installer la version officielle WCF sur une machine où une version CTP précoce de WCF a été installé, mais pas complètement désinstallé.  
  
 ServiceModelReg.exe ne peut pas nettoyer les entrées de versions antérieures ; il ne peut pas non plus enregistrer les entrées de la nouvelle version. La seule solution de contournement est d’éditer manuellement machine.config. Vous pouvez localiser ce fichier à l’endroit suivant.  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 Si vous exécutez WCF sur une machine 64 bits, vous devez également modifier le même fichier à cet endroit.  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 Localisez tous les nœuds XML dans ce fichier qui se réfèrent à "System.ServiceModel, Version 2.0.0.0", supprimez-les et nœuds pour enfants. Enregistrez le fichier et réexécutez ServiceModelReg.exe afin de résoudre ce problème.  
  
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
