---
title: Technologies .NET Framework non disponibles sur .NET Core
description: Découvrir les technologies .NET Framework non disponibles sur .NET Core
author: cartermp
ms.author: mairaw
ms.date: 04/30/2019
ms.openlocfilehash: 4a798e85adc056b09761bd17b5d9a143643e77ad
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397621"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologies .NET Framework non disponibles sur .NET Core

Certaines technologies mises à la disposition des bibliothèques .NET Framework ne sont pas utilisables avec .NET Core, notamment les AppDomains, Remoting, la sécurité d’accès du code (CAS) et la transparence de la sécurité. Si vos bibliothèques reposent sur une ou plusieurs de ces technologies, envisagez les autres approches décrites ci-dessous. Pour plus d’informations sur la compatibilité des API, l’équipe CoreFX conserve la [Liste des modifications de comportement/arrêts de compatibilité et des API déconseillées/héritées](https://github.com/dotnet/corefx/wiki/ApiCompat) sur GitHub.

Le fait qu’une technologie ou une API ne soit pas implémentée pour le moment ne signifie pas que l’absence de prise en charge soit intentionnelle. Vous devez tout d’abord rechercher .NET Core dans les dépôts GitHub pour savoir si le problème que vous rencontrez est lié à la conception. Si vous n’en obtenez pas la confirmation, ouvrez un dossier dans le [dépôt de consignation des problèmes dotnet/corefx](https://github.com/dotnet/corefx/issues) de GitHub pour réclamer des API et des technologies spécifiques. Les [demandes de portage dans les problèmes](https://github.com/dotnet/corefx/labels/port-to-core) sont marquées avec l’étiquette `port-to-core`.

## <a name="appdomains"></a>AppDomains

Les domaines d’application (AppDomains) isolent les applications les unes des autres. Ils requièrent la prise en charge du runtime et sont généralement assez onéreux. La création de domaines d’application supplémentaires n’est pas prise en charge. Nous ne prévoyons pas d’ajouter cette fonctionnalité par la suite. Pour l’isolation du code, nous recommandons d’utiliser des processus distincts ou des conteneurs à la place. Pour le chargement dynamique d’assemblys, nous recommandons la nouvelle classe <xref:System.Runtime.Loader.AssemblyLoadContext>.

Pour faciliter la migration de code à partir du .NET Framework, .NET Core expose une partie de la surface d’API <xref:System.AppDomain>. Certaines API fonctionnent normalement (par exemple, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), certains membres ne font rien (par exemple, <xref:System.AppDomain.SetCachePath%2A>) et d’autres lèvent <xref:System.PlatformNotSupportedException> (par exemple, <xref:System.AppDomain.CreateDomain%2A>). Vérifiez les types que vous utilisez dans la [`System.AppDomain`source de référence](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) du [dépôt GitHub dotnet/corefx](https://github.com/dotnet/corefx) en veillant à sélectionner la branche qui correspond à la version que vous avez implémentée.

## <a name="remoting"></a>Communication à distance

.NET Remoting a été identifié comme architecture problématique. Elle est utilisée pour la communication entre AppDomains, qui n’est plus prise en charge. Par ailleurs, Remoting requiert la prise en charge du runtime, dont la maintenance est coûteuse. C’est pourquoi .NET Remoting n’est pas pris en charge sur .NET Core, et nous ne prévoyons pas d’ajouter sa prise en charge à l’avenir.

Pour la communication entre processus, envisagez de mettre en place des mécanismes de communication interprocessus (IPC) à la place de Remoting, par exemple la classe <xref:System.IO.Pipes> ou la classe <xref:System.IO.MemoryMappedFiles.MemoryMappedFile>.

Pour la communication entre ordinateurs, utilisez plutôt une solution réseau. Choisissez de préférence un protocole de texte brut à faible charge, par exemple HTTP. Le [serveur web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), utilisé par ASP.NET Core, est une possibilité. Vous pouvez également envisager d’utiliser <xref:System.Net.Sockets> pour les scénarios réseau sur différents ordinateurs. Pour plus d’options, consultez la page [Projets de développement .NET open source : messagerie](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>sécurité d'accès du code (CAS, Code Access Security)

Le sandboxing, qui s’appuie sur le runtime ou le framework pour limiter les ressources utilisées ou exécutées par une application gérée ou une bibliothèque, [n’est pas pris en charge sur .NET Framework](~/docs/framework/misc/code-access-security.md) ni, par conséquent, sur .NET Core. Les cas sont trop nombreux dans .NET Framework et le runtime où une élévation des privilèges se produit pour continuer à considérer la sécurité d’accès du code comme une limite de sécurité. En outre, la sécurité du code complique l’implémentation et a souvent a des implications en matière de performances d’exactitude pour les applications qui ne prévoient pas de l’utiliser.

Servez-vous des limites de sécurité fournies par le système d’exploitation, comme la virtualisation, les conteneurs ou les comptes d’utilisateurs, pour exécuter des processus avec l’ensemble de privilèges minimal.

## <a name="security-transparency"></a>Transparence de la sécurité

Tout comme la sécurité d’accès du code, la transparence de la sécurité sépare le code sandbox du code critique de sécurité d’une manière déclarative, mais [n’est plus prise en charge en tant que limite de sécurité](~/docs/framework/misc/security-transparent-code.md). Cette fonctionnalité est très utilisée par Silverlight. 

Utilisez les limites de sécurité fournies par le système d’exploitation, comme la virtualisation, les conteneurs ou des comptes d’utilisateurs, pour exécuter des processus avec l’ensemble de privilèges le plus petit possible.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

System.EnterpriseServices (COM+) n’est pas pris en charge par .NET Core.

>[!div class="step-by-step"]
>[Next](third-party-deps.md)
