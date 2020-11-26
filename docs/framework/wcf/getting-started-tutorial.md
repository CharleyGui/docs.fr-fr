---
title: 'Didacticiel : prise en main des applications Windows Communication Foundation'
description: Ces didacticiels fournissent une introduction à la création d’applications WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 620a83260f01e27a19b19227165695a621c88e5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238234"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Didacticiel : prise en main des applications Windows Communication Foundation

Les séries de didacticiels suivantes présentent l’expérience de programmation Windows Communication Foundation (WCF). L’utilisation de ces didacticiels dans l’ordre vous donnera une compréhension de la procédure à suivre pour créer des applications WCF. Une fois que vous avez terminé, vous disposerez d’un service WCF en cours d’exécution et d’un client WCF qui appelle le service.

Ce didacticiel part du principe que vous utilisez Visual Studio comme environnement de développement. Si vous utilisez un autre environnement de développement, ignorez les instructions spécifiques à Visual Studio.

Pour obtenir des exemples d’applications WCF que vous pouvez télécharger et exécuter, consultez [Windows Communication Foundation des exemples](samples/index.md). Pour obtenir une présentation des exemples, consultez la rubrique prise en main de l' [exemple](samples/getting-started-sample.md).

Pour plus d’informations sur la création de services et de clients, consultez [programmation WCF de base](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>Didacticiels WCF

Les trois premiers didacticiels décrivent comment définir un contrat de service WCF, comment l’implémenter et comment l’héberger. Le service que vous créez est auto-hébergé dans une application console. Vous pouvez également héberger des services sous Microsoft Internet Information Services (IIS). Pour plus d’informations, consultez [Comment : héberger un service WCF dans IIS](feature-details/how-to-host-a-wcf-service-in-iis.md). Bien que vous utilisiez du code pour configurer le service dans le didacticiel, vous pouvez également [configurer des services dans un fichier de configuration](configuring-services-using-configuration-files.md).

- [Didacticiel : définir un contrat de service](how-to-define-a-wcf-service-contract.md)

    Vous créez un contrat WCF avec une interface définie par l’utilisateur. Ce contrat définit les fonctionnalités exposées par le service.

- [Didacticiel : implémenter un contrat de service](how-to-implement-a-wcf-contract.md)

    Une fois que vous avez défini un contrat, vous devez l’implémenter avec une classe de service.

- [Didacticiel : héberger et exécuter un service de base](how-to-host-and-run-a-basic-wcf-service.md)

    Configurez un point de terminaison pour le service et hébergez le service dans une application console. Pour qu’un service devienne actif, vous devez le configurer et l’héberger dans un environnement d’exécution. Cet environnement d’exécution crée le service et contrôle son contexte et sa durée de vie.

Les deux didacticiels suivants décrivent la création, la configuration et l’utilisation d’une application cliente pour appeler les opérations exposées par le service. Les services publient les métadonnées qui définissent les informations dont une application cliente a besoin pour communiquer avec le service. Visual Studio automatise le processus d’accès à ces métadonnées et l’utilise pour créer l’application cliente pour le service. Si vous décidez de ne pas utiliser Visual Studio, vous pouvez utiliser l' [outil ServiceModel Metadata Utility (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) à la place.

- [Didacticiel : créer un client](how-to-create-a-wcf-client.md)

    Récupérer les métadonnées pour la création d’un proxy client WCF à partir d’un service WCF. Vous récupérez les métadonnées à l’aide de Visual Studio pour ajouter une référence de service ou vous pouvez utiliser l’outil utilitaire de métadonnées ServiceModel. Vous spécifiez le point de terminaison que le client utilise pour accéder au service.

- [Didacticiel : utiliser un client](how-to-use-a-wcf-client.md)

    Utilisez le proxy client WCF pour appeler les opérations de service.

## <a name="reference"></a>Informations de référence

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble conceptuelle](conceptual-overview.md)
- [Guide de la documentation](guide-to-the-documentation.md)
- [Qu’est-ce que Windows Communication Foundation](whats-wcf.md)
- [Informations détaillées sur les fonctionnalités WCF](feature-details/index.md)
- [Cycle de vie de programmation de base](basic-programming-lifecycle.md)
- [Génération de clients](building-clients.md)
- [Programmation WCF de base](basic-wcf-programming.md)
- [Comment : créer un contrat duplex](feature-details/how-to-create-a-duplex-contract.md)
- [Comment : accéder aux services à l’aide d’un contrat duplex](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Outil utilitaire de métadonnées ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Comment : utiliser Svcutil.exe pour télécharger des documents de métadonnées](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Comment : publier les métadonnées d’un service à l’aide d’un fichier de configuration](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Utilisation de liaisons pour configurer des services et des clients](using-bindings-to-configure-services-and-clients.md)
- [Exemple de prise en main](samples/getting-started-sample.md)
- [Exemples de Windows Communication Foundation](samples/index.md)
- [Self-Host](samples/self-host.md)
