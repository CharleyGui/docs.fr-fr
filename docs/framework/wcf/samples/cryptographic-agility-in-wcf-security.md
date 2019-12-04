---
title: Agilité de chiffrement dans la sécurité WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714921"
---
# <a name="cryptographic-agility-in-wcf-security"></a>Agilité de chiffrement dans la sécurité WCF

Cet exemple montre comment spécifier dans un algorithme standard/personnalisé pour fournir une implémentation de chiffrement agile dans un service et un client Windows Communication Foundation (WCF). Cet exemple est composé des projets suivants :

**Service**

Il s’agit d’un service WCF auto-hébergé qui implémente l’interface `ICalculator` et sécurise le point de terminaison à l’aide de la <xref:System.ServiceModel.WSHttpBinding> avec une session sécurisée et une session fiable désactivée. Le service définit une classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.

**Client**

Il s’agit d’un client WCF qui accède au service après une authentification réussie. Il appelle les opérations exposées par l'interface `ICalculator` et implémentées par le service. Le client définit également la même classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.

## <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. Ouvrez la solution CryptoAgility. sln dans Visual Studio 2012.

2. Appuyez sur Ctrl+Maj+B pour générer la solution.

3. Ouvrez l’Explorateur de fichiers et accédez au répertoire \WCF\Basic\Security\CryptoAgility\Service\bin et exécutez le fichier service. exe avec des privilèges d’administrateur en cliquant avec le bouton droit sur service. exe et en sélectionnant **exécuter en tant qu’administrateur**.

4. Accédez au répertoire \WCF\Basic\Security\CryptoAgility\Client\bin et exécutez le fichier client.exe normalement.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>Voir aussi

- [Sécurité Windows Communication Foundation](../feature-details/security.md)
