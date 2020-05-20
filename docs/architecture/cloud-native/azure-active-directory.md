---
title: Azure Active Directory
description: Architecture des applications .NET natives Cloud pour Azure | Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 03f5ea8e84bc3c4a2a88a63d4b109aabf0c64f36
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614277"
---
# <a name="azure-active-directory"></a>Azure Active Directory

Microsoft Azure Active Directory (Azure AD) offre une gestion des identités et des accès en tant que service. Les clients l’utilisent pour configurer et gérer les utilisateurs, les informations à leur sujet, les personnes qui peuvent accéder à ces informations, les personnes autorisées à les gérer et les applications qui peuvent y accéder. AAD peut authentifier les utilisateurs pour les applications configurées pour l’utiliser, en fournissant une expérience d’authentification unique (SSO). Il peut être utilisé seul ou intégré à Windows AD en local.

Azure AD est conçu pour le Cloud. Il s’agit véritablement d’une solution d’identité Cloud native qui utilise une API Graph basée sur REST et une syntaxe OData pour les requêtes, contrairement à Windows AD, qui utilise LDAP. En local Active Directory pouvez synchroniser les attributs utilisateur dans le Cloud à l’aide des services de synchronisation des identités, ce qui permet à l’authentification d’avoir lieu dans le Cloud à l’aide de Azure AD. L’authentification peut également être configurée via Connect pour revenir à la Active Directory locale via ADFS pour être effectuée par Windows AD en local.

Azure AD prend en charge les écrans de connexion de la société, l’authentification multilingue et les proxys d’applications basés sur le Cloud qui sont utilisés pour fournir l’authentification unique pour les applications hébergées localement. Il offre différents types de rapports de sécurité et de fonctionnalités d’alerte.

## <a name="references"></a>References

- [Plateforme d’identité Microsoft](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Précédent](authentication-authorization.md) 
> [Suivant](identity-server.md)
