---
title: Publication d’un package NuGet
description: Meilleures pratiques recommandées pour la publication de bibliothèques .NET dans NuGet.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 9c8442b52ed2c54d2fb3368a2e886c5fc2b19148
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640768"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="a9fe5-103">Publication d’un package NuGet</span><span class="sxs-lookup"><span data-stu-id="a9fe5-103">Publishing a NuGet package</span></span>

<span data-ttu-id="a9fe5-104">Les packages NuGet sont publiés et utilisés à partir de référentiels de packages.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="a9fe5-105">Bien que NuGet.org soit le référentiel le plus largement connu et utilisé, il existe de nombreux endroits où publier des packages NuGet :</span><span class="sxs-lookup"><span data-stu-id="a9fe5-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="a9fe5-106">**[NuGet.org](https://www.nuget.org/)**  est le principal référentiel en ligne pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="a9fe5-107">Tous les packages sur NuGet.org sont accessibles à tous.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="a9fe5-108">Par défaut, Visual Studio utilise NuGet.org comme source de package, et pour de nombreux développeurs NuGet.org est le seul référentiel de package avec lequel ils interagissent.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="a9fe5-109">NuGet.org est l’endroit idéal pour publier des packages stables et des packages en préversion que vous souhaitez soumettre à l’avis de la communauté.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="a9fe5-110">**[MyGet](https://myget.org/)**  est un service de référentiel qui prend en charge des flux de packages personnalisés pour les projets open source.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="a9fe5-111">Un flux personnalisé public MyGet est l’endroit idéal pour publier des packages en préversion créés par votre service d’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="a9fe5-112">MyGet commercialise également des flux privés.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="a9fe5-113">Un **[flux local](/nuget/hosting-packages/local-feeds)** vous permet de traiter un dossier comme un référentiel de packages et rend les fichiers `*.nupkg` de ce dossier accessibles par NuGet.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="a9fe5-114">Un flux local est utile pour tester un package NuGet avant sa publication sur NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="a9fe5-115">NuGet.org [n’autorise pas la suppression d’un package](/nuget/policies/deleting-packages) une fois qu’il est chargé.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="a9fe5-116">Un package peut être retiré de la liste afin qu’il ne soit pas publiquement visible dans l’interface utilisateur, mais le `*.nupkg` peut toujours être téléchargé lors de la restauration.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="a9fe5-117">En outre, nuget.org n’autorise pas les versions de package en double.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="a9fe5-118">Pour corriger un package NuGet comportant une erreur, vous devez retirer de la liste le package incorrect, incrémenter le numéro de version, puis publier une nouvelle version du package.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="a9fe5-119">**✔️ À FAIRE** [Publier des packages stables et des packages en préversion](/nuget/create-packages/publish-a-package) que vous souhaitez soumettre à l’avis de la communauté sur NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="a9fe5-120">**✔️ À ENVISAGER** Publier des packages en préversion pour un flux MyGet à partir d’une build d’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="a9fe5-121">**✔️ À ENVISAGER** Tester des packages dans votre environnement de développement à l’aide d’un flux local ou MyGet.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="a9fe5-122">Vérifiez le fonctionnement du package, puis publiez-le sur NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="a9fe5-123">Sécurité de NuGet.org</span><span class="sxs-lookup"><span data-stu-id="a9fe5-123">NuGet.org security</span></span>

<span data-ttu-id="a9fe5-124">Il est important d’empêcher les personnes mal intentionnées d’accéder à votre compte NuGet pour y télécharger une version malveillante de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="a9fe5-125">NuGet.org propose une authentification à deux facteurs et des notifications par e-mail lors de la publication d’un package.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="a9fe5-126">Activez ces fonctionnalités une fois connecté à NuGet.org sur la page **Paramètres du compte**.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="a9fe5-127">![texte de remplacement](./media/publish-nuget-package/nuget-2fa.png "Sécurité du compte NuGet")</span><span class="sxs-lookup"><span data-stu-id="a9fe5-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="a9fe5-128">**✔️ À FAIRE** Utiliser un compte Microsoft pour vous connecter à NuGet.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="a9fe5-129">**✔️ À FAIRE** Activer l’authentification à deux facteurs pour accéder à NuGet.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="a9fe5-130">**✔️ À FAIRE** Activer la notification par e-mail lorsqu’un package est publié.</span><span class="sxs-lookup"><span data-stu-id="a9fe5-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a9fe5-131">[Précédent](sourcelink.md)
>[Suivant](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="a9fe5-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>
