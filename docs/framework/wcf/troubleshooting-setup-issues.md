---
title: Résolution des problèmes d’installation
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 2cd9ced4f0780b1a6f63e4a5833e20ac91870121
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121581"
---
# <a name="troubleshoot-setup-issues"></a>Problèmes de configuration de dépannage

Cet article décrit comment dépanner Windows Communication Foundation (WCF) mettre en place des problèmes.  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Certaines clés de registre Windows Communication Foundation ne sont pas réparées par l'exécution d'une opération de réparation MSI sur le .NET Framework 3.0  
 Si vous supprimez l'une des clés de registre suivantes :  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0  
  
 Les clés ne sont pas recréées si vous exécutez la réparation en utilisant l’installateur .NET Framework 3.0 lancé à partir de la applet **Add/Remove Programs** in **Control Panel**. Pour recréer ces clés correctement, l'utilisateur doit désinstaller, puis réinstaller le .NET Framework 3.0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>La corruption des services WMI bloque l'installation du fournisseur WMI Windows Communication Foundation pendant l'installation du package .NET Framework 3.0  
 La corruption des services WMI peut bloquer l'installation du fournisseur WMI Windows Communication Foundation. Pendant l'installation, le programme d'installation de Windows Communication Foundation ne peut pas enregistrer le fichier WCF .mof à l'aide du composant mofcomp.exe. La section suivante présente la liste des symptômes :  
  
1. .NET Framework 3.0 s'installe correctement, mais le fournisseur WMI WCF n'est pas enregistré.  
  
2. Un événement d'erreur apparaît dans le journal des événements de l'application qui référence les problèmes d'enregistrement du fournisseur WMI pour WCF, ou d'exécution du fichier mofcomp.exe.  
  
3. Le fichier journal d'installation dd_wcf_retCA* qui se trouve dans le répertoire % temp% de l'utilisateur contient des références relatives à l'échec de l'enregistrement du fournisseur WMI WCF.  
  
4. Une exception du type de celle présentée ci-après peut être répertoriée dans le journal des événements ou le fichier journal de suivi de l'installation :  
  
     ServiceModelReg [11:09:59:046] : System.ApplicationException : résultat 3 inattendu lors de l'exécution de E:\WINDOWS\system32\wbem\mofcomp.exe avec "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"  
  
     ou :  
  
     ServiceModelReg [07:19:33:843] : System.TypeInitializationException : l'initialiseur de type de 'System.Management.ManagementPath' a levé une exception. ---> System.Runtime.InteropServices.COMException (0x80040154): La récupération de l’usine de classe COM pour composant avec CLSID CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA) n’a pas manqué en raison de l’erreur suivante: 80040154.  
  
     ou :  
  
     ServiceModelReg [07:19:32:750] : System.IO.FileNotFoundException : impossible de charger le fichier ou l'assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' ou l'une de ses dépendances. Le système ne peut pas trouver le fichier spécifié.  
  
     Nom de fichier : 'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Suivez la procédure suivante pour résoudre le problème décrit précédemment.  
  
1. Exécutez le [service public de diagnostic WMI](https://www.microsoft.com/download/details.aspx?id=7684) pour réparer le service WMI. Pour plus d’informations sur l’utilisation de cet outil, voir [WMI Diagnosis Utility](https://docs.microsoft.com/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).  
  
 Réparer l’installation .NET Framework 3.0 en utilisant la pommet **Add/Remove Programs** située dans **le panneau de contrôle**, ou désinstaller/réinstaller le cadre .NET 3.0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>La réparation du .NET Framework 3.0 après l'installation du .NET Framework 3.5 supprime les éléments de configuration introduits par le .NET Framework 3.5 dans machine.config  
 Si vous faites une réparation de .NET Framework 3.0 après avoir installé .NET Framework 3.5, les éléments de configuration introduits par .NET Framework 3.5 in machine.config sont supprimés. Cependant, web.config reste intact. La solution de contournement est de réparer .NET Framework 3.5 après cela via ARP, ou d’utiliser `/c` [l’outil d’enregistrement des services workFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) avec le commutateur.  
  
 [Outil d’enregistrement des services de flux de travail (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) peut être trouvé à %windir%-Microsoft.NET-framework-v3.5 ou %windir%-Microsoft.NET-framework64-v3.5  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Configurer IIS correctement pour WCF/WF Webhost après l'installation du .NET Framework 3.5  
 Lorsque l’installation .NET Framework 3.5 ne parvient pas à configurer d’autres paramètres de configuration IIS liés au WCF, elle enregistre une erreur dans le journal d’installation et se poursuit. Toute tentative d'exécution des applications WorkflowServices échoue, étant donné que les paramètres de configuration sont manquants. Par exemple, le chargement du service xoml ou de règles peut échouer.  
  
 Pour résoudre ce problème, utilisez [l’outil d’enregistrement des services WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) avec le `/c` commutateur pour configurer correctement les cartes de script IIS sur la machine. [Outil d’enregistrement des services de flux de travail (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) peut être trouvé à %windir%-Microsoft.NET-framework-v3.5 ou %windir%-Microsoft.NET-framework64-v3.5  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Impossible de charger le type 'System.ServiceModel.Activation.HttpModule' de l’assemblage 'System.ServiceModel, Version 3.0.0.0, Culture’neutre, PublicKeyToken-b77a5c561934e089'  
 Cette erreur se produit si .NET Framework 4 est installé, puis WCF HTTP Activation est activé. Pour résoudre le problème, exécutez la ligne de commande suivante de l’intérieur de l’invite de commande de développeur pour Visual Studio :  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Voir aussi

- [Instructions d’ajustement](./samples/set-up-instructions.md)
