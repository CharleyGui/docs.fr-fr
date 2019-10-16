---
title: Cycle de vie de la programmation de base
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: fe578ba3c655c9c9ea8398b9b2e4d4f974153c8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320827"
---
# <a name="basic-programming-lifecycle"></a>Cycle de vie de la programmation de base
Windows Communication Foundation (WCF) permet aux applications de communiquer si elles se trouvent sur le même ordinateur, sur Internet ou sur différentes plateformes d’application. Cette rubrique décrit les tâches requises pour générer une application WCF. Pour obtenir un exemple d’application fonctionnel, consultez [prise en main didacticiel](getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Tâches de base  
 Les tâches de base à accomplir sont les suivantes, dans l’ordre :  
  
1. Définition du contrat de service. Un contrat de service spécifie la signature d'un service, les données qu'il échange et les autres données requises contractuellement. Pour plus d’informations, consultez [conception de contrats de service](designing-service-contracts.md).  
  
2. Implémentation du contrat. Pour implémenter un contrat de service, créez une classe qui implémente le contrat et spécifiez les comportements personnalisés requis pour le runtime. Pour plus d’informations, consultez [implémentation de contrats de service](implementing-service-contracts.md).  
  
3. Configuration du service en spécifiant les informations de points de terminaison et d'autres informations de comportement. Pour plus d’informations, consultez [Configuration des services](configuring-services.md).  
  
4. Hébergement du service. Pour plus d’informations, consultez [services d’hébergement](hosting-services.md).  
  
5. Création d'une application cliente. Pour plus d’informations, consultez [génération de clients](building-clients.md).  
  
 Bien que les rubriques de cette section suivent cet ordre, certains scénarios ne commencent pas au début. Par exemple, si vous souhaitez générer un client pour un service préexistant, démarrez à l'étape 5. Autrement, si vous générez un service que d'autres utiliseront, vous pouvez ignorer l'étape 5.  
  
 Une fois que vous êtes familiarisé avec le développement de contrats de service, vous pouvez également lire la [Présentation de l’extensibilité](introduction-to-extensibility.md). Si vous rencontrez des problèmes avec votre service, vérifiez le Guide de [démarrage rapide de WCF Troubleshooting](wcf-troubleshooting-quickstart.md) pour déterminer si d’autres ont des problèmes identiques ou similaires.  
  
## <a name="see-also"></a>Voir aussi

- [Implémentation de contrats de service](implementing-service-contracts.md)
