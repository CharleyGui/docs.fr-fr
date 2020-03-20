---
title: Mécanismes de contrôle d'accès
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: b423dac4d8324069eb1825666419b23b5afdca63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185494"
---
# <a name="access-control-mechanisms"></a>Mécanismes de contrôle d'accès
Vous pouvez contrôler l’accès de plusieurs manières avec Windows Communication Foundation (WCF). Cette rubrique présente brièvement les différents mécanismes et suggère quand utiliser chacun ; elle a pour objectif de vous aider à sélectionner le mécanisme approprié à utiliser. Les technologies d'accès sont répertoriées par ordre de complexité. La plus simple est le <xref:System.Security.Permissions.PrincipalPermissionAttribute> ; la plus complexe est le modèle d'identité.  
  
 En plus de ces mécanismes, l’usurpation d’identité et la délégation avec WCF sont expliquées dans [Délégation et Usurpion](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> permet de restreindre l'accès à une méthode de service. Lorsque l’attribut est appliqué à une méthode, il peut être utilisé pour exiger l’identité ou l’adhésion d’un appelant spécifique à un groupe Windows ou ASP.NET rôle. Si le client est authentifié à l'aide d'un certificat X.509, il bénéficie d'une identité principale qui se compose du nom du sujet auquel s'ajoute l'empreinte numérique du certificat.  
  
 Utilisez l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> pour contrôler l'accès aux ressources sur l'ordinateur où le service s'exécute et pour contrôler si les utilisateurs du service feront toujours partie du même domaine Windows sur lequel le service s'exécute. Vous pouvez créer facilement des groupes Windows disposant de niveaux d'accès spécifiés (tels qu'aucun, lecture seule ou lecture et écriture).  
  
 Pour plus d’informations sur l’utilisation de l’attribut, voir [Comment : Restreindre l’accès à la classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Pour plus d’informations sur l’identité, voir [Identité de service et authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Fournisseur d'appartenances ASP.NET  
 Une caractéristique de ASP.NET est le fournisseur d’adhésion. Bien que le fournisseur d'appartenances ne soit pas techniquement un mécanisme de contrôle d'accès, il permet de contrôler l'accès au service en limitant le jeu d'identités possibles qui peuvent accéder au point de terminaison du service. La fonctionnalité d’appartenance inclut une base de données qui peut être remplie avec des associations nom d’utilisateur/mot de passe qui permettent aux utilisateurs d’un site Web d’établir des comptes avec le site. Pour accéder à un service qui utilise le fournisseur d’abonnement, un utilisateur doit se connecter avec son nom d’utilisateur et son mot de passe.  
  
> [!NOTE]
> Vous devez d’abord remplir la base de données à l’aide de la fonction ASP.NET avant qu’un service WCF puisse l’utiliser à des fins d’autorisation.  
  
 Vous pouvez également utiliser la fonction d’adhésion si vous disposez déjà d’une base de données d’adhésion à partir d’un site Web ASP.NET existant et que vous souhaitez permettre aux mêmes utilisateurs d’utiliser votre service, autorisés avec les mêmes noms d’utilisateur et mots de passe.  
  
 Pour plus d’informations sur l’utilisation de la fonction d’adhésion dans un service WCF, voir [Comment: Utilisez le fournisseur de ASP.NET d’adhésion](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Fournisseur de rôle ASP.NET  
 Une autre caractéristique de ASP.NET est la capacité de gérer l’autorisation en utilisant des rôles. Le fournisseur de rôles ASP.NET permet à un développeur de créer des rôles pour les utilisateurs et d’affecter chaque utilisateur à un rôle ou à un rôle. Comme pour le fournisseur d’adhésion, les rôles et les affectations sont stockés dans une base de données et peuvent être peuplés à l’aide d’outils fournis par une mise en œuvre particulière du fournisseur de ASP.NET rôle. Comme pour la fonction d’adhésion, les développeurs WCF peuvent utiliser les informations contenues dans la base de données pour autoriser les utilisateurs de services par rôles. Par exemple, ils peuvent utiliser le fournisseur de rôle en association avec le mécanisme de contrôle d'accès `PrincipalPermissionAttribute` décrit précédemment.  
  
 Vous pouvez également utiliser le fournisseur de rôles ASP.NET si vous disposez d’une base de données existante ASP.NET fournisseur de rôles et que vous souhaitez utiliser le même ensemble de règles et d’affectations d’utilisateurs dans votre service WCF.  
  
 Pour plus d’informations sur l’utilisation de la fonction fournisseur de rôle, voir [Comment: Utilisez le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Gestionnaire d'autorisations  
 Une autre fonctionnalité combine le gestionnaire d’autorisation (AzMan) avec le fournisseur de rôle ASP.NET pour autoriser les clients. Lorsque ASP.NET héberge un service Web, AzMan peut être intégré dans l’application afin que l’autorisation du service soit effectuée par l’intermédiaire d’AzMan. ASP.NET gestionnaire de rôle fournit une API qui vous permet de gérer les rôles d’application, d’ajouter et de supprimer les utilisateurs des rôles, et de vérifier l’adhésion au rôle, mais il ne vous permet pas de demander si un utilisateur est autorisé à effectuer une tâche ou une opération désignée. AzMan vous permet de définir des opérations individuelles et de les associer dans des tâches. Grâce à AZMan, outre les contrôles de rôle, vous pouvez également vérifier si un utilisateur peut effectuer une tâche. L’affectation des rôles et l’autorisation des tâches peuvent être configurées en dehors de l’application ou effectuées par programme au sein de l’application. Le composant logiciel enfichable Microsoft Management Console (MMC) d'administration AzMan permet aux administrateurs de modifier les tâches qu'un rôle peut effectuer au moment de l'exécution et de gérer l'appartenance aux rôles de chaque utilisateur.  
  
 Vous pouvez également utiliser AzMan et le fournisseur de rôles ASP.NET si vous avez déjà accès à une installation AzMan existante et souhaitez autoriser vos utilisateurs de services en utilisant les fonctionnalités de la combinaison AzMan/fournisseur de rôles.  
  
 Pour plus d’informations sur AzMan et le fournisseur de rôles ASP.NET, voir [Comment: Utilisez le gestionnaire de l’autorisation (AzMan) avec ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)). Pour plus d’informations sur l’utilisation d’AzMan et le fournisseur de rôle pour les services WCF, voir [Comment: Utilisez le fournisseur de rôle ASP.NET gestionnaire d’autorisation avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Modèle d'identité  
 Le modèle d'identité est un ensemble d'API qui vous permettent de gérer des revendications et des stratégies pour autoriser des clients. Le modèle d'identité vous permet d'examiner chaque revendication incluse dans les informations d'identification que l'appelant a utilisée pour s'authentifier auprès du service, de comparer les revendications au jeu de stratégies pour le service et d'accorder ou de refuser l'accès en fonction de cette comparaison.  
  
 Utilisez le modèle d'identité si vous avez besoin d'un contrôle précis et de la capacité de définir des critères spécifiques avant d'accorder l'accès. Par exemple, lorsque vous utilisez <xref:System.Security.Permissions.PrincipalPermissionAttribute>, le critère est simplement que l'identité de l'utilisateur est authentifiée et que l'utilisateur appartient à un rôle spécifique. En revanche, le modèle d'identité vous permet de créer une stratégie stipulant que l'utilisateur doit être majeur et qu'il doit posséder un permis de conduire valide pour pouvoir être autorisé à consulter un document.  
  
 Par exemple, vous pouvez tirer parti du contrôle d'accès basé sur revendication du modèle d'identité lorsque vous utilisez des informations d'identification de fédération dans le scénario de jeton émis. Pour plus d’informations sur la fédération et les jetons émis, voir [Fédération et les jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Pour plus d’informations sur le modèle d’identité, voir [Gérer les réclamations et l’autorisation avec le modèle d’identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Guide pratique pour restreindre l’accès avec la classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Comment : utiliser le fournisseur de rôle du Gestionnaire d'autorisations ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Délégation et emprunt d'identité](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
