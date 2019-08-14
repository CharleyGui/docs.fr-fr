---
title: 'Procédure : installer et configurer des composants d’activation WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: aed6cb71ac3ccd7af5423cdb8ccc43133bbe5337
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972031"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Procédure : installer et configurer des composants d’activation WCF

Cette rubrique décrit les étapes nécessaires à la configuration du service d’activation des processus Windows (également appelé was [!INCLUDE[wv](../../../../includes/wv-md.md)] ) sur les services Host Windows Communication Foundation (WCF) qui ne communiquent pas sur les protocoles réseau http. Les sections suivantes définissent les étapes pour cette configuration :

- Installez (ou confirmez l’installation de) les composants d’activation WCF.

- Configurer le service WAS pour prendre en charge un protocole non HTTP. La procédure suivante configure [!INCLUDE[wv](../../../../includes/wv-md.md)] pour l'activation TCP.

Après l’installation et la configuration de was [, consultez Procédure: Héberger un service WCF dans](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) was pour les procédures de création d’un service WCF qui expose un point de terminaison non-http qui utilise was.

## <a name="to-install-the-wcf-non-http-activation-components"></a>Pour installer les composants d'activation non HTTP WCF

1. Cliquez sur le bouton **Démarrer** , puis sur **panneau de configuration**.

2. Cliquez sur **programmes**, puis sur **programmes et fonctionnalités**.

3. Dans le menu **tâches** , cliquez sur **activer ou désactiver des fonctionnalités Windows**.

4. Recherchez le nœud WinFX, sélectionnez-le, puis développez-le.

5. Sélectionnez la zone **composants d’activation non HTTP WCF** et enregistrez le paramètre.

## <a name="to-configure-the-was-to-support-tcp-activation"></a>Pour configurer le service WAS pour prendre en charge l'activation TCP

1. Pour assurer la prise en charge de l'activation de net.tcp, le site Web par défaut doit d'abord être lié à un port net.tcp. Pour ce faire, vous pouvez utiliser Appcmd. exe, qui est installé avec l’ensemble d’outils de gestion d’IIS 7,0. Dans une fenêtre d'invite de commandes au niveau de l'administrateur, exécutez la commande suivante.

    ```
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > Cette commande est une ligne unique de texte. Cette commande ajoute une liaison de site net.tcp au site Web par défaut qui écoute sur le port TCP 808, quel que soit le nom d’hôte.

2. Bien que toutes les applications d'un site partagent la même liaison net.tcp, chacune d'elle peut activer de manière individuelle la prise en charge net.pipe. Afin d'activer net.tcp pour l'application, exécutez la commande suivante à partir d'une invite de commandes au niveau de l'administrateur.

    ```
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > Cette commande est une ligne unique de texte. Cette commande permet d’accéder\<à l’application >*WCF*à l’aide `http://localhost/<WCF Application>` de et `net.tcp://localhost/<WCF Application>`de.

     Supprimez la liaison de site net.tcp que vous avez ajoutée dans le cadre de cet exemple.

     Pour des raisons pratiques, les deux étapes suivantes sont implémentées dans le fichier de commandes RemoveNetTcpSiteBinding.cmd situé dans le répertoire de l'exemple.

    1. Supprimez le protocole net.tcp de la liste des protocoles activés en exécutant la commande suivante dans une invite de commandes au niveau de l'administrateur.

        ```
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > Cette commande est une ligne unique de texte.

    2. Supprimez la liaison du site net.tcp en exécutant la commande suivante dans une invite de commandes de niveau élevé :

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > Cette commande est une ligne unique de texte.

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Pour supprimer net.tcp de la liste des protocoles actifs

1. Pour supprimer net.tcp de la liste des protocoles actifs, exécutez la commande suivante dans une invite de commandes au niveau de l'administrateur.

    ```
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > Cette commande est une ligne unique de texte.

## <a name="to-remove-the-nettcp-site-binding"></a>Pour supprimer la liaison de site net.tcp

1. Pour supprimer la liaison de site net.tcp, exécutez la commande suivante dans une fenêtre d’invite de commandes au niveau de l’administrateur.

    ```
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > Cette commande est une ligne unique de texte.

## <a name="see-also"></a>Voir aussi

- [Activation TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Activation MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [Activation de NamedPipe](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201276)
