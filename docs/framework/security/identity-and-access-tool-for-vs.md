---
title: Outil Identité et accès pour Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: d58cca13dc3ac67742e5371aed628a6a680e61e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045425"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Outil Identité et accès pour Visual Studio 2012
Cette rubrique décrit le nouvel outil Identité et accès pour Visual Studio 11. Vous pouvez télécharger cet outil à partir de l’URL <https://go.microsoft.com/fwlink/?LinkID=245849> suivante : ou directement à partir de Visual Studio 11 en recherchant « Identity » directement dans le gestionnaire d’extensions.  
  
 L'outil Identité et accès pour Visual Studio 11 offre une expérience très simplifiée du développement et met en avant les points suivants :  
  
- À l'aide de ce nouvel outil, vous pouvez développer l'utilisation de types de projet d'application Web et IIS Express cibles.  
  
- Contrairement à l'authentification de protection générale uniquement, avec ce nouvel outil, vous pouvez spécifier la page de découverte/le contrôleur d'accueil de domaine local (ou tout autre point de terminaison qui gère l'expérience d'authentification dans votre application) et WIF configure toutes les demandes non authentifiées pour y accéder, au lieu de les rediriger vers STS.  
  
- L'outil inclut un service d'émission de jetons de sécurité (STS) de test qui s'exécute sur l'ordinateur local lorsque vous lancez une session de débogage. Par conséquent, vous n'avez plus à créer de projets STS personnalisés et à les manipuler pour obtenir les revendications dont vous avez besoin pour tester vos applications. Les types et les valeurs de revendication sont entièrement personnalisables.  
  
- Vous pouvez modifier les paramètres courants directement via l'interface utilisateur de l'outil, sans avoir à modifier le fichier web.config.  
  
- Vous pouvez générer la fédération avec les services ADFS (Active Directory Federation Services) (AD FS) 2.0 (ou d'autres fournisseurs de WS-Federation) dans un même écran.  
  
- L’outil utilise les fonctionnalités de Windows Azure Access Control Service (ACS) avec une simple liste de cases à cocher pour tous les fournisseurs d’identité que vous souhaitez utiliser : Facebook, Google, Live ID, Yahoo !, n’importe quel fournisseur OpenID et n’importe quel fournisseur WS-Federation. Sélectionnez les fournisseurs d'identité, cliquez sur OK, puis sur F5, et votre application et ACS sont automatiquement configurés et votre application de test prend en charge ACS.  
  
## <a name="see-also"></a>Voir aussi

- [Fonctionnalités WIF](wif-features.md)
