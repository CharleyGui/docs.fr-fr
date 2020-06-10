---
title: "Comment : utiliser l'outil de configuration de modèle de service COM+"
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: f9e761bafd84726b51a2010a932c68c67c37f899
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595282"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Comment : utiliser l'outil de configuration de modèle de service COM+
Une fois que vous avez sélectionné un mode d'hébergement approprié, utilisez l'outil en ligne de commande de configuration de modèle de service COM+ (ComSvcConfig.exe) pour configurer les interfaces d'application qui seront exposées en tant que services Web.  
  
> [!NOTE]
> Vous devez être administrateur sur l’ordinateur pour exécuter chacune des tâches suivantes.  
  
 Lorsque vous utilisez ComSvcConfig.exe sur un ordinateur Windows 7 pour configurer un service Web de façon à utiliser la dernière version de modèle de service (v4.5), exécutez les étapes suivantes :  
  
1. Affectez à la clé de Registre `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` une valeur DWORD 0x00000001.  
  
2. Exécutez comsvcconfig.exe.  
  
3. Rétablissez la valeur par défaut de la clé de Registre ajoutée à l'étape 1, ou supprimez -la si elle n'existait pas.  
  
> [!IMPORTANT]
> Il est important de rétablir cette clé de Registre. Il s'agit d'une clé de compatibilité. Le fait de ne pas rétablir cette modification peut provoquer des problèmes avec d'autres applications .NET en cours de exécution sur l'ordinateur.  
  
> [!WARNING]
> Quand vous utilisez ComSvcConfig. exe/install sur un ordinateur Windows 8, une boîte de dialogue s’affiche indiquant « une application sur votre PC a besoin de la fonctionnalité Windows suivante : .NET Framework 3,5 (comprend .NET 2,0 et .NET 3,0 » si .NET Framework 3,5 n’est pas installée. Cette boîte de dialogue peut être ignorée. Vous pouvez aussi affecter à la clé de Registre OnlyUseLatestCLR la valeur DWORD 0x00000001.  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a>Pour ajouter une interface à l’ensemble des interfaces exposées en tant que services Web, à l’aide du mode d’hébergement COM+  
  
- Exécutez ComSvcConfig avec les options `/install` et `/hosting:complus`, comme illustré dans l'exemple suivant.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     La commande ajoute l'interface `IFinances` du composant `ItemOrders.IFinancial` (depuis l'application COM+ OnlineStore) à l'ensemble des interfaces qui seront exposées en tant que services Web. Le service utilise le mode d'hébergement COM+, et requiert par conséquent l'activation d'application explicite.  
  
     Si le caractère générique astérisque ( \* ) peut être utilisé pour le composant et l’interface, évitez de l’utiliser, car vous souhaiterez peut-être exposer uniquement les fonctionnalités sélectionnées en tant que service Web. En cas d'exécution avec une version ultérieure de ce composant, l'utilisation du caractère générique peut exposer involontairement des interfaces qui étaient peut-être absentes lorsque la syntaxe de configuration a été déterminée.  
  
     L'option /verbose fait en sorte que l'outil affiche des avertissements en plus des éventuelles erreurs.  
  
     Le contrat pour le service exposé contiendra toutes les méthodes de l'interface `IFinances`.  
  
## <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a>Pour ajouter uniquement des méthodes spécifiques d’une interface à l’ensemble des interfaces exposées en tant que services Web, à l’aide du mode d’hébergement COM+  
  
- Exécutez ComSvcConfig avec les options `/install` et `/hosting:complus` et avec la désignation explicite des méthodes requises, comme illustré dans l'exemple suivant.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     La commande ajoute uniquement les méthodes `Credit` et `Debit` de l'interface `IFinances` comme opérations au contrat de service exposé. Toutes les autres méthodes sur l'interface seront omises du contrat et ne pourront pas être appelées à partir de clients de service Web.  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-web-hosting-mode"></a>Pour ajouter une interface à l’ensemble des interfaces exposées en tant que services Web, à l’aide du mode d’hébergement Web  
  
- Exécutez ComSvcConfig avec les options `/install` et `/hosting:was`, comme illustré dans l'exemple suivant.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     La commande ajoute l'interface `IStockLevels` sur le composant `ItemInventory.Warehouse` (depuis l'application COM+ OnlineWarehouse) à l'ensemble des interfaces qui seront exposées en tant que services Web. Le service étant hébergé sur le Web dans le répertoire virtuel OnlineWarehouse des services Internet (IIS) plutôt que dans COM+, l'application est activée automatiquement selon les besoins.  
  
     Pour utiliser la configuration hébergée sur le Web dans un processus, l'application COM+ doit être configurée pour s'exécuter en tant qu'application bibliothèque plutôt qu'application serveur à l'aide de la console d'administration Services de composants. Les applications configurées en tant qu'applications serveur utilisent le mode hébergé sur le Web standard et effectuent un saut de processus pour traiter chaque demande.  
  
     L'option `/mex` ajoute un point de terminaison de service Échange de métadonnées (MEX) supplémentaire qui utilise le même transport que le point de terminaison de service de l'application pour prendre en charge les clients qui souhaitent récupérer une définition de contrat à partir du service.  
  
## <a name="to-remove-a-web-service-for-a-specified-interface"></a>Pour supprimer un service Web pour une interface spécifiée  
  
- Exécutez ComSvcConfig avec l'option `/uninstall`, comme illustré dans l'exemple suivant.  
  
    ```console  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     La commande supprime l'interface `IFinances` sur le composant `ItemOrders.Financial` (de l'application COM+ OnlineStore).  
  
## <a name="to-list-currently-exposed-interfaces"></a>Pour répertorier les interfaces exposées actuellement  
  
- Exécutez ComSvcConfig avec l'option `/list`, comme illustré dans l'exemple suivant.  
  
    ```console  
    ComSvcConfig.exe /list  
    ```  
  
     La commande répertoire les interfaces actuellement exposées, avec l’adresse correspondante et les détails de liaison, avec comme étendue l’ordinateur local.  
  
## <a name="to-list-specific-currently-exposed-interfaces"></a>Pour répertorier des interfaces spécifiques exposées actuellement  
  
- Exécutez ComSvcConfig avec l'option `/list`, comme illustré dans l'exemple suivant.  
  
    ```console  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     La commande répertoire les interfaces hébergées par COM+ exposées actuellement, avec l’adresse correspondante et les détails de liaison, pour l’application COM+ OnlineStore sur l’ordinateur local.  
  
## <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Pour afficher une aide sur les options qui peuvent être utilisées avec l'utilitaire  
  
- Exécutez ComSvcConfig à l'aide de l'option /?, tel qu'illustré par l'exemple suivant.  
  
    ```console  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’intégration aux applications COM+](integrating-with-com-plus-applications-overview.md)
