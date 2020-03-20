---
title: 'Tutorial: Démarrer avec les applications de la Fondation De communication Windows'
description: Ces tutoriels fournissent une introduction pour la création d’applications WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184123"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Tutorial: Démarrer avec les applications de la Fondation De communication Windows
La série de tutoriels ci-après vous présente l’expérience de programmation de la Windows Communication Foundation (WCF). Travailler à travers ces tutoriels dans l’ordre vous donnera une compréhension d’introduction des étapes nécessaires pour créer des applications WCF. Une fois que vous aurez terminé, vous aurez un service WCF en cours d’exécution et un client WCF qui appelle le service.

Le tutoriel suppose que vous utilisez Visual Studio comme environnement de développement. Si vous utilisez un autre environnement de développement, ignorez les instructions spécifiques au Studio Visuel.

Pour les exemples d’applications WCF que vous pouvez télécharger et exécuter, voir [échantillons de la Fondation Windows Communication](samples/index.md). Pour une introduction aux échantillons, voir [Getting started sample](samples/getting-started-sample.md).

Pour plus d’informations approfondies sur la création de services et de clients, consultez [la programmation de base WCF](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>Tutoriels WCF

Les trois premiers tutoriels décrivent comment définir un contrat de service WCF, comment le mettre en œuvre, et comment l’héberger. Le service que vous créez est auto-hébergé dans une application de console. Vous pouvez également héberger des services sous Microsoft Internet Information Services (IIS). Pour plus d’informations, voir [Comment : Organiser un service WCF en IIS](feature-details/how-to-host-a-wcf-service-in-iis.md). Bien que vous utilisiez du code pour configurer le service dans le tutoriel, vous pouvez également [configurer les services dans un fichier de configuration](configuring-services-using-configuration-files.md).

- [Tutorial: Définir un contrat de service](how-to-define-a-wcf-service-contract.md)

    Vous créez un contrat WCF avec une interface définie par l’utilisateur. Ce contrat définit la fonctionnalité que le service expose.

- [Tutorial: Mettre en œuvre un contrat de service](how-to-implement-a-wcf-contract.md)

    Après avoir défini un contrat, vous devez le mettre en œuvre avec une classe de service.

- [Tutorial: Hôte et exécuter un service de base](how-to-host-and-run-a-basic-wcf-service.md)

    Configurer un point de terminaison pour le service et héberger le service dans une application de console. Pour qu’un service devienne actif, vous devez le configurer et l’héberger dans un environnement de temps d’exécution. Cet environnement de run-time crée le service et contrôle son contexte et sa durée de vie.

Les deux tutoriels suivants décrivent comment créer, configurer et utiliser une application client pour appeler les opérations que le service expose. Les services publient les métadonnées qui définissent les informations dont une application cliente a besoin pour communiquer avec le service. Visual Studio automatise le processus d’accès à ces métadonnées et l’utilise pour construire l’application client pour le service. Si vous décidez de ne pas utiliser Visual Studio, vous pouvez utiliser [l’outil ServiceModel Metadata Utility (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) à la place.

- [Tutorial: Créer un client](how-to-create-a-wcf-client.md)

    Récupérez les métadonnées pour la création d’un proxy client WCF à partir d’un service WCF. Vous récupérez les métadonnées en utilisant Visual Studio pour ajouter une référence de service ou vous pouvez utiliser l’outil ServiceModel Metadata Utility. Vous spécifiez le point de terminaison que le client utilise pour accéder au service.

- [Tutorial: Utilisez un client](how-to-use-a-wcf-client.md)

    Utilisez le proxy client WCF pour appeler les opérations de service.

## <a name="reference"></a>Informations de référence

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Voir aussi

- [Aperçu conceptuel](conceptual-overview.md)
- [Guide de la documentation](guide-to-the-documentation.md)
- [Qu’est-ce que Windows Communication Foundation](whats-wcf.md)
- [Détails de la fonctionnalité WCF](feature-details/index.md)
- [Cycle de vie de programmation de base](basic-programming-lifecycle.md)
- [Construire des clients](building-clients.md)
- [Programmation de base de WCF](basic-wcf-programming.md)
- [Comment : Créer un contrat en duplex](feature-details/how-to-create-a-duplex-contract.md)
- [Comment : Accéder aux services avec un contrat en duplex](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Outil utilitaire de métadonnées de service de service (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Comment: Utilisez Svcutil.exe pour télécharger des documents de métadonnées](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Comment : Publier des métadonnées pour un service à l’aide d’un fichier de configuration](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Utilisation de liaisons pour configurer les services et les clients](using-bindings-to-configure-services-and-clients.md)
- [Commencer l’échantillon](samples/getting-started-sample.md)
- [Échantillons de la Fondation Windows Communication](samples/index.md)
- [Auto-hébergement](samples/self-host.md)
