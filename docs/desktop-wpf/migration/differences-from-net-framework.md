---
title: Différences entre .NET Framework et .NET Core
description: Décrit les différences entre l’implémentation .NET Framework de Windows Presentation Foundation WPF (WPF) et .NET Core WPF. Lors de la migration de votre application, vous devez tenir compte de ces incompatibilités.
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

Cet article décrit les différences entre les Windows Presentation Foundation (WPF) sur .NET Core et les .NET Framework. WPF pour .NET Core est une [infrastructure Open source](https://github.com/dotnet/wpf) dupliquée à partir du WPF d’origine pour .NET Framework code source.

Il existe quelques fonctionnalités de .NET Framework que .NET Core ne prend pas en charge. Pour plus d’informations sur les technologies non prises en charge, consultez [.NET Framework technologies indisponibles sur .net Core](../../core/porting/net-framework-tech-unavailable.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>Projets de style SDK

.NET Core utilise des fichiers de projet de type SDK. Ces fichiers projet sont différents des fichiers de projet .NET Framework traditionnels gérés par Visual Studio. Pour migrer vos applications WPF .NET Framework vers .NET Core, vous devez convertir vos projets. Pour plus d’informations, consultez [migrer des applications WPF vers .net Core 3,0](convert-project-from-net-framework.md).

## <a name="nuget-package-references"></a>Références du package NuGet

Si votre application .NET Framework répertorie ses dépendances NuGet dans un fichier *packages. config* , migrez vers le [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format :

1. Dans Visual Studio, ouvrez le volet **Explorateur de solutions** .
1. Dans votre projet WPF, cliquez avec le bouton droit sur **packages. config** > **migre packages. config vers PackageReference**.

![Mise à niveau vers PackageReference](media/differences-from-net-framework/package-reference-migration.png)

Une boîte de dialogue s’affiche avec les dépendances NuGet de niveau supérieur calculées et vous demandant quels autres packages NuGet doivent être promus au niveau supérieur. Sélectionnez **OK** et le fichier *packages. config* sera supprimé du projet et `<PackageReference>` les éléments seront ajoutés au fichier projet.

Lorsque votre projet utilise `<PackageReference>`, les packages ne sont pas stockés localement dans un dossier *packages* , ils sont stockés globalement. Ouvrez le fichier projet et supprimez `<Analyzer>` tous les éléments référencés dans le dossier *packages* . Ces analyseurs sont automatiquement inclus avec les références de package NuGet.

## <a name="code-access-security"></a>Sécurité d'accès du code

La sécurité d’accès du code (CAS) n’est pas prise en charge par .NET Core ou WPF pour .NET Core. Toutes les fonctionnalités liées à l’autorité de certification sont traitées en supposant un niveau de confiance totale. WPF pour .NET Core supprime le code lié au CAS. La surface de l’API publique de ces types existe toujours pour garantir que les appels à ces types fonctionnent correctement.

Les types liés à l’autorité de certification publiquement définis ont été déplacés hors des assemblys WPF et dans les assemblys de la bibliothèque .NET de base. Le transfert de type des assemblys WPF est défini sur le nouvel emplacement des types déplacés.

| Assembly source | Assembly cible | Type                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *System. Security. Permissions. dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System.Xaml.dll* | *System. Security. Permissions. dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System.Xaml.dll* | *System. Windows. extension. dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> Afin de réduire le frottement sur le Portage, les fonctionnalités de stockage et de récupération des informations relatives aux propriétés suivantes ont été conservées dans le `XamlAccessLevel` type.
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>Étapes suivantes

- [Découvrez comment porter une application WPF .NET Framework vers .NET Core.](convert-project-from-net-framework.md)
