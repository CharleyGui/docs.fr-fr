---
title: Différences entre .NET Framework et .NET Core
description: Décrit les différences entre la mise en œuvre du cadre .NET de Windows Presentation Foundation (WPF) et .NET Core WPF. Lorsque vous migrez votre application, vous devez tenir compte de ces incompatibilités.
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072206"
---
# <a name="differences-in-wpf"></a>Différences dans WPF

Cet article décrit les différences entre Windows Presentation Foundation (WPF) sur .NET Core et .NET Framework. WPF pour .NET Core est un [cadre open-source](https://github.com/dotnet/wpf) fourche à partir du WPF original pour le code source cadre .NET.

Il ya quelques caractéristiques de .NET Framework que .NET Core ne prend pas en charge. Pour plus d’informations sur les technologies non-supportées, voir [.NET Technologies du Cadre indisponibles sur .NET Core](../../core/porting/net-framework-tech-unavailable.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>Projets de style SDK

.NET Core utilise des fichiers de projets de style SDK. Ces fichiers de projet sont différents des fichiers traditionnels du projet cadre .NET gérés par Visual Studio. Pour migrer vos applications .NET Framework WPF vers .NET Core, vous devez convertir vos projets. Pour plus d’informations, voir [les applications Migrate WPF à .NET Core 3.0](convert-project-from-net-framework.md).

## <a name="nuget-package-references"></a>Références du package NuGet

Si votre application .NET Framework répertorie ses dépendances NuGet [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) dans un fichier *packages.config,* migrez vers le format :

1. Dans Visual Studio, ouvrez la vitre **Solution Explorer.**
1. Dans votre projet WPF, right-click **packages.config** > **Migrate packages.config à PackageReference**.

![Mise à niveau vers PackageReference](media/differences-from-net-framework/package-reference-migration.png)

Un dialogue apparaîtra montrant les dépendances NuGet calculées de haut niveau et demandant quels autres paquets NuGet devraient être promus au plus haut niveau. Sélectionnez **OK** et le fichier *packages.config* sera `<PackageReference>` supprimé du projet et des éléments seront ajoutés au fichier du projet.

Lorsque votre `<PackageReference>`projet utilise, les paquets ne sont pas stockés localement dans un dossier *Paquets,* ils sont stockés dans le monde entier. Ouvrez le fichier `<Analyzer>` de projet et supprimez tous les éléments qui se référaient au dossier *Paquets.* Ces analyseurs sont automatiquement inclus dans les références du paquet NuGet.

## <a name="code-access-security"></a>Sécurité d'accès du code

Code Access Security (CAS) n’est pas pris en charge par .NET Core ou WPF pour .NET Core. Toutes les fonctionnalités liées à la SAE sont traitées en supposant une pleine confiance. WPF pour .NET Core supprime le code lié à la SAE. La surface publique de l’API de ces types existe toujours pour s’assurer que les appels dans ces types réussissent.

Les types de CAS définis publiquement ont été déplacés hors des assemblées du WPF pour se rendre aux assemblées de la bibliothèque Core .NET. Les assemblages WPF ont le type-forwarding réglé à la nouvelle position des types déplacés.

| Assemblage de source | Assemblage cible | Type                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *System.security.Permissions.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System.Xaml.dll* | *System.security.Permissions.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System.Xaml.dll* | *System.Windows.Extension.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> Afin de minimiser le frottement du portage, la fonctionnalité de stockage et `XamlAccessLevel` de récupération des informations relatives aux propriétés suivantes a été conservée dans le type.
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>Étapes suivantes

- [Apprenez à porter une application .NET Framework WPF à .NET Core.](convert-project-from-net-framework.md)
