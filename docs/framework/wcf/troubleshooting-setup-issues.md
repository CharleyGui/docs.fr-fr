---
title: Résolution des problèmes d’installation
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 76d8752f8bcfcb94b77a60be60e13a66436e76b8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549651"
---
# <a name="troubleshoot-setup-issues"></a>Résoudre les problèmes d’installation

Cet article explique comment résoudre les problèmes de configuration de Windows Communication Foundation (WCF).  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Certaines clés de registre Windows Communication Foundation ne sont pas réparées par l'exécution d'une opération de réparation MSI sur le .NET Framework 3.0  
 Si vous supprimez l'une des clés de registre suivantes :  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0  
  
 Les clés ne sont pas recréées si vous exécutez la réparation à l’aide du programme d’installation .NET Framework 3,0 lancé à partir de l’applet **Ajout/suppression de programmes** du **panneau de configuration**. Pour recréer ces clés correctement, l'utilisateur doit désinstaller, puis réinstaller le .NET Framework 3.0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>La corruption des services WMI bloque l'installation du fournisseur WMI Windows Communication Foundation pendant l'installation du package .NET Framework 3.0  
 La corruption des services WMI peut bloquer l'installation du fournisseur WMI Windows Communication Foundation. Pendant l'installation, le programme d'installation de Windows Communication Foundation ne peut pas enregistrer le fichier WCF .mof à l'aide du composant mofcomp.exe. La section suivante présente la liste des symptômes :  
  
1. .NET Framework 3.0 s'installe correctement, mais le fournisseur WMI WCF n'est pas enregistré.  
  
2. Un événement d'erreur apparaît dans le journal des événements de l'application qui référence les problèmes d'enregistrement du fournisseur WMI pour WCF, ou d'exécution du fichier mofcomp.exe.  
  
3. Le fichier journal d'installation dd_wcf_retCA* qui se trouve dans le répertoire % temp% de l'utilisateur contient des références relatives à l'échec de l'enregistrement du fournisseur WMI WCF.  
  
4. Une exception du type de celle présentée ci-après peut être répertoriée dans le journal des événements ou le fichier journal de suivi de l'installation :  
  
     ServiceModelReg [11:09:59:046] : System.ApplicationException : résultat 3 inattendu lors de l'exécution de E:\WINDOWS\system32\wbem\mofcomp.exe avec "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"  
  
     ou :  
  
     ServiceModelReg [07:19:33:843] : System.TypeInitializationException : l'initialiseur de type de 'System.Management.ManagementPath' a levé une exception. ---> System. Runtime. InteropServices. COMException (0x80040154) : la récupération de la fabrique de classe COM pour le composant avec le CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} a échoué en raison de l’erreur suivante : 80040154.  
  
     ou :  
  
     ServiceModelReg [07:19:32:750] : System.IO.FileNotFoundException : impossible de charger le fichier ou l'assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' ou l'une de ses dépendances. Le système ne peut pas trouver le fichier spécifié.  
  
     Nom de fichier : 'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Suivez la procédure suivante pour résoudre le problème décrit précédemment.  
  
1. Exécutez le [WMI Diagnosis Utility](https://www.microsoft.com/download/details.aspx?id=7684) pour réparer le service WMI. Pour plus d’informations sur l’utilisation de cet outil, consultez [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v=msdn.10)).  
  
 Réparez l’installation .NET Framework 3,0 à l’aide de l’applet **Ajout/suppression de programmes** située dans le **panneau de configuration**, ou désinstallez/réinstallez le .NET Framework 3,0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>La réparation du .NET Framework 3.0 après l'installation du .NET Framework 3.5 supprime les éléments de configuration introduits par le .NET Framework 3.5 dans machine.config  
 Si vous effectuez une réparation de .NET Framework 3,0 après avoir installé .NET Framework 3,5, les éléments de configuration introduits par .NET Framework 3,5 dans machine.config sont supprimés. Cependant, web.config reste intact. La solution consiste à réparer .NET Framework 3,5 après cela via ARP, ou à utiliser l' [outil Workflow Service Registration (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) avec le `/c` commutateur.  
  
 [L’outil d’inscription du service de flux de travail (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) est disponible dans emplacement%windir%\Microsoft.NET\Framework\v3.5\ ou%windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Configurer IIS correctement pour WCF/WF Webhost après l'installation du .NET Framework 3.5  
 Lorsque .NET Framework installation de 3,5 ne parvient pas à configurer d’autres paramètres de configuration IIS liés à WCF, il enregistre une erreur dans le journal d’installation et continue. Toute tentative d'exécution des applications WorkflowServices échoue, étant donné que les paramètres de configuration sont manquants. Par exemple, le chargement du service xoml ou de règles peut échouer.  
  
 Pour contourner ce problème, utilisez l' [outil d’inscription du service de flux de travail (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) avec le `/c` commutateur pour configurer correctement les mappages de scripts IIS sur l’ordinateur. [L’outil d’inscription du service de flux de travail (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) est disponible dans emplacement%windir%\Microsoft.NET\Framework\v3.5\ ou%windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Impossible de charger le type’System. ServiceModel. activation. HttpModule’à partir de l’assembly’System. ServiceModel, version 3.0.0.0, culture = neutral, PublicKeyToken = b77a5c561934e089 '  
 Cette erreur se produit si .NET Framework 4 est installé et que l’activation HTTP WCF est activée. Pour résoudre le problème, exécutez la ligne de commande suivante à partir de la Invite de commandes développeur pour Visual Studio :  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Voir aussi

- [Instructions d'installation](./samples/set-up-instructions.md)
