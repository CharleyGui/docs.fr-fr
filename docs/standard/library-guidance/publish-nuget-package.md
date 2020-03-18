---
title: Publication d’un package NuGet
description: Meilleures pratiques recommandées pour la publication de bibliothèques .NET dans NuGet.
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744554"
---
# <a name="publishing-a-nuget-package"></a>Publication d’un package NuGet

Les packages NuGet sont publiés et utilisés à partir de référentiels de packages. Bien que NuGet.org soit le référentiel le plus largement connu et utilisé, il existe de nombreux endroits où publier des packages NuGet :

* **[NuGet.org](https://www.nuget.org/)** est le principal référentiel en ligne pour les packages NuGet. Tous les packages sur NuGet.org sont accessibles à tous. Par défaut, Visual Studio utilise NuGet.org comme source de package, et pour de nombreux développeurs NuGet.org est le seul référentiel de package avec lequel ils interagissent. NuGet.org est l’endroit idéal pour publier des packages stables et des packages en préversion que vous souhaitez soumettre à l’avis de la communauté.

* **[MyGet](https://myget.org/)** est un service de référentiel qui prend en charge des flux de packages personnalisés pour les projets open source. Un flux personnalisé public MyGet est l’endroit idéal pour publier des packages en préversion créés par votre service d’intégration continue. MyGet commercialise également des flux privés.

* Un **[flux local](/nuget/hosting-packages/local-feeds)** vous permet de traiter un dossier comme un référentiel de packages et rend les fichiers `*.nupkg` de ce dossier accessibles par NuGet. Un flux local est utile pour tester un package NuGet avant sa publication sur NuGet.org.

> [!NOTE]
> NuGet.org [n’autorise pas la suppression d’un package](/nuget/policies/deleting-packages) une fois qu’il est chargé. Un package peut être retiré de la liste afin qu’il ne soit pas publiquement visible dans l’interface utilisateur, mais le `*.nupkg` peut toujours être téléchargé lors de la restauration. En outre, nuget.org n’autorise pas les versions de package en double. Pour corriger un package NuGet comportant une erreur, vous devez retirer de la liste le package incorrect, incrémenter le numéro de version, puis publier une nouvelle version du package.

✔️ NE [publiez des paquets stables et des paquets de pré-version](/nuget/create-packages/publish-a-package) que vous voulez obtenir des commentaires de la communauté sur NuGet.org.

✔️ À ENVISAGER Publier des packages en préversion pour un flux MyGet à partir d’une build d’intégration continue.

✔️ À ENVISAGER Tester des packages dans votre environnement de développement à l’aide d’un flux local ou MyGet. Vérifiez le fonctionnement du package, puis publiez-le sur NuGet.org.

## <a name="nugetorg-security"></a>Sécurité de NuGet.org

Il est important d’empêcher les personnes mal intentionnées d’accéder à votre compte NuGet pour y télécharger une version malveillante de votre bibliothèque. NuGet.org propose une authentification à deux facteurs et des notifications par e-mail lors de la publication d’un package. Activez ces fonctionnalités une fois connecté à NuGet.org sur la page **Paramètres du compte**.

![texte alt](./media/publish-nuget-package/nuget-2fa.png "Sécurité du compte NuGet")

✔️ À FAIRE Utiliser un compte Microsoft pour vous connecter à NuGet.

✔️ À FAIRE Activer l’authentification à deux facteurs pour accéder à NuGet.

✔️ À FAIRE Activer la notification par e-mail lorsqu’un package est publié.

>[!div class="step-by-step"]
>[Suivant précédent](sourcelink.md)
>[Next](versioning.md)
