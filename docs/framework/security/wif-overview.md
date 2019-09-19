---
title: Vue d'ensemble de Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 5f723345-7270-49e2-b638-b3a34bd40517
author: BrucePerlerMS
ms.openlocfilehash: c9420ce641da32edc6196be0743d967446a14947
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045004"
---
# <a name="windows-identity-foundation-45-overview"></a>Vue d'ensemble de Windows Identity Foundation 4.5
Windows Identity Foundation 4.5 est un ensemble de classes .NET Framework permettant d'implémenter une identité basée sur des revendications dans vos applications. Vous pouvez ainsi exploiter plus facilement les avantages des applications et des services qui prennent en charge les revendications. WIF 4.5 peut être utilisé dans toute application Web ou service Web qui utilise la version 4.5 de. NET Framework ou une version ultérieure. WIF est simplement une partie de la famille des logiciels d'identité fédérée de Microsoft qui implémente la vision partagée de secteur en fonction de normes ouvertes. L’identité fédérée comprend trois composants : [Services de fédération Active Directory®](https://go.microsoft.com/fwlink/?LinkID=247516) (AD FS) 2,0, [Windows Azure Access Control services](https://go.microsoft.com/fwlink/?LinkID=247517) (ACS) et WIF. Ensemble, ces trois éléments forment le cœur de la nouvelle plateforme d'accès et d'identité Cloud basée sur les revendications de Microsoft.  
  
 Pour plus d’informations sur WIF, consultez le [site Web Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=149009) dans le centre de sécurité pour développeurs sur MSDN. Pour une introduction à la création d’applications à l’aide de WIF, consultez [programmation de Windows Identity Foundation](https://www.microsoftpressstore.com/store/programming-windows-identity-foundation-9780735627185) by Vittorio Bertocci (publié par Microsoft Press).  
  
## <a name="wif-45-features"></a>Fonctionnalités WIF 4.5  
 WIF 4.5 est une infrastructure permettant de générer des applications orientées identités. L'infrastructure abrège les protocoles WS-Trust et WS-Federation et présente aux développeurs des API pour générer des applications qui prennent en charge les revendications et, si nécessaire, les services d'émission de jetons de sécurité (STS). Les applications peuvent utiliser WIF pour traiter les jetons émis par STS, comme AD FS 2.0 et ACS, et prennent des décisions basées sur l'identité dans l'application Web ou le service Web.  
  
 WIF 4.5 comprend les principales fonctionnalités suivantes :  
  
- Génération d'applications prenant en charge les revendications (applications de partie de confiance). WIF aide les développeurs à générer les applications prenant en charge les revendications. En plus de fournir un modèle de revendications, il fournit aux développeurs d'application un ensemble complet d'API pour aider à prendre des décisions d'accès utilisateur basées sur des revendications.  WIF fournit également aux développeurs une expérience cohérente en programmation qu'ils choisissent de créer leurs applications dans ASP.NET ou dans des environnements WCF.  
  
- Génération d'une prise en charge de délégation d'identité dans les applications qui prennent en charge les revendications.  WIF offre la possibilité de gérer les identités de demandeurs d'origine à travers les limites de plusieurs services. Cette fonction peut être obtenue soit en utilisant  la fonction « ActAs » ou « OnBehalfOf » dans l'infrastructure et elle offre aux développeurs la possibilité d'ajouter la prise en charge de délégation d'identité dans leurs applications qui prennent en charge les revendications.  
  
- Création de STS personnalisés.  WIF simplifie énormément la génération d'un STS personnalisé qui prend en charge le protocole WS-Trust. Ce type de STS porte également le nom de STS actif.  
  
     En outre, l'infrastructure fournit également la prise en charge de la création d'un STS qui prend en charge WS-Federation pour activer les client de navigateur Web. Ce STS porte également le nom de STS passif.  
  
- Nouvel outil Identité et accès pour Visual Studio 11 qui vous permet de protéger votre application avec l'identité basée sur les revendications et d'accepter des utilisateurs de plusieurs fournisseurs d'identité. Vous pouvez télécharger cet outil WIF à partir de l’URL <https://go.microsoft.com/fwlink/?LinkID=245849> suivante : ou directement à partir de Visual Studio 11 en recherchant « Identity » directement dans le gestionnaire d’extensions. Pour plus d’informations, consultez [Identity and Access Tool pour Visual Studio 2012](identity-and-access-tool-for-vs.md).  
  
 WIF prend en charge les principaux scénarios suivants :  
  
- Fédération.  WIF permet d'activer la fédération entre deux partenaires ou plus. Sa prise en charge de la génération d'applications qui prennent en charge les revendications (RPS) et des STS personnalisés aident les développeurs à accomplir ce scénario.  
  
- Délégation d'identité.  WIF facilite la gestion des identités à travers les limites de service afin que les développeurs puissent réaliser un scénario de délégation d'identité.  
  
- Mise en place de l'authentification. Les exigences en termes d’authentification pour différentes ressources dans une application peuvent varier. WIF fournit aux développeurs la capacité de générer des applications qui peuvent imposer des spécifications incrémentielles d'authentification (par exemple : la connexion initiale avec le nom d'utilisateur/l'authentification par mot de passe, puis l'authentification par carte à puce).  
  
 À l'aide de WIF, vous tirerez plus facilement des avantages du modèle d'identité basé sur des revendications. Pour plus d’informations, consultez le [livre blanc sur Windows Identity Foundation pour les développeurs](https://download.microsoft.com/download/7/d/0/7d0b5166-6a8a-418a-addd-95ee9b046994/windowsidentityfoundationwhitepaperfordevelopers-rtw.pdf).
