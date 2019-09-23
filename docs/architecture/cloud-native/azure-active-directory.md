---
title: Azure Active Directory
description: Architecture des applications .NET natives Cloud pour Azure | Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 207043507a9052c47683383a98cef6417a1a2740
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183692"
---
# <a name="azure-active-directory"></a><span data-ttu-id="146dd-103">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="146dd-103">Azure Active Directory</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="146dd-104">Microsoft Azure Active Directory (Azure AD) offre une gestion des identités et des accès en tant que service.</span><span class="sxs-lookup"><span data-stu-id="146dd-104">Microsoft Azure Active Directory (Azure AD) offers identity and access management as a service.</span></span> <span data-ttu-id="146dd-105">Les clients l’utilisent pour configurer et gérer les utilisateurs, les informations à leur sujet, les personnes qui peuvent accéder à ces informations, les personnes autorisées à les gérer et les applications qui peuvent y accéder.</span><span class="sxs-lookup"><span data-stu-id="146dd-105">Customers use it to configure and maintain who users are, what information to store about them, who can access that information, who can manage it, and what apps can access it.</span></span> <span data-ttu-id="146dd-106">AAD peut authentifier les utilisateurs pour les applications configurées pour l’utiliser, en fournissant une expérience d’authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="146dd-106">AAD can authenticate users for applications configured to use it, providing a single sign-on (SSO) experience.</span></span> <span data-ttu-id="146dd-107">Il peut être utilisé seul ou intégré à Windows AD en local.</span><span class="sxs-lookup"><span data-stu-id="146dd-107">It can be used on its own or be integrated with Windows AD running on premises.</span></span>

<span data-ttu-id="146dd-108">Azure AD est conçu pour le Cloud.</span><span class="sxs-lookup"><span data-stu-id="146dd-108">Azure AD is built for the cloud.</span></span> <span data-ttu-id="146dd-109">Il s’agit véritablement d’une solution d’identité Cloud native qui utilise une API Graph basée sur REST et une syntaxe OData pour les requêtes, contrairement à Windows AD, qui utilise LDAP.</span><span class="sxs-lookup"><span data-stu-id="146dd-109">It's truly a cloud-native identity solution that uses a REST-based Graph API and OData syntax for queries, unlike Windows AD, which uses LDAP.</span></span> <span data-ttu-id="146dd-110">En local Active Directory pouvez synchroniser les attributs utilisateur dans le Cloud à l’aide des services de synchronisation des identités, ce qui permet à l’authentification d’avoir lieu dans le Cloud à l’aide de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="146dd-110">On premises Active Directory can sync user attributes to the cloud using Identity Sync Services, allowing all authentication to take place in the cloud using Azure AD.</span></span> <span data-ttu-id="146dd-111">L’authentification peut également être configurée via Connect pour revenir à la Active Directory locale via ADFS pour être effectuée par Windows AD en local.</span><span class="sxs-lookup"><span data-stu-id="146dd-111">Alternately, authentication can be configured via Connect to pass back to local Active Directory via ADFS to be completed by Windows AD on premises.</span></span>

<span data-ttu-id="146dd-112">Azure AD prend en charge les écrans de connexion de la société, l’authentification multilingue et les proxys d’applications basés sur le Cloud qui sont utilisés pour fournir l’authentification unique pour les applications hébergées localement.</span><span class="sxs-lookup"><span data-stu-id="146dd-112">Azure AD supports company branded sign-in screens, multi-factory authentication, and cloud-based application proxies that are used to provide SSO for applications hosted on premises.</span></span> <span data-ttu-id="146dd-113">Il offre différents types de rapports de sécurité et de fonctionnalités d’alerte.</span><span class="sxs-lookup"><span data-stu-id="146dd-113">It offers different kinds of security reporting and alert capabilities.</span></span>

## <a name="references"></a><span data-ttu-id="146dd-114">Références</span><span class="sxs-lookup"><span data-stu-id="146dd-114">References</span></span>

- [<span data-ttu-id="146dd-115">Plateforme d’identité Microsoft</span><span class="sxs-lookup"><span data-stu-id="146dd-115">Microsoft identity platform</span></span>](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="146dd-116">[Précédent](authentication-authorization.md)
>[Suivant](identity-server.md)</span><span class="sxs-lookup"><span data-stu-id="146dd-116">[Previous](authentication-authorization.md)
[Next](identity-server.md)</span></span>
