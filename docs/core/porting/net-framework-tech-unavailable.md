---
title: Technologies .NET Framework non disponibles sur .NET Core
titleSuffix: ''
description: Découvrir les technologies .NET Framework non disponibles sur .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: bd2488de653ecdfed261100b4c9019bea58fcab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092939"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologies .NET Framework non disponibles sur .NET Core

Plusieurs technologies disponibles pour les bibliothèques cadres .NET ne sont pas disponibles pour une utilisation avec .NET Core, tels que AppDomains, Remoting, Code Access Security (CAS), Security Transparency, et System.EnterpriseServices. Si vos bibliothèques reposent sur une ou plusieurs de ces technologies, envisagez les autres approches décrites ci-dessous. Pour plus d’informations sur la compatibilité API, voir [.NET Core changements de rupture](../compatibility/breaking-changes.md).

Le fait qu’une technologie ou une API ne soit pas implémentée pour le moment ne signifie pas que l’absence de prise en charge soit intentionnelle. Rechercher les référentiels GitHub pour .NET Core pour voir si un problème particulier que vous rencontrez est par la conception. Si vous ne trouvez pas un tel indicateur, déposez un problème dans le [référentiel pointnet/runtime](https://github.com/dotnet/runtime/issues) pour demander des API et des technologies spécifiques. Les questions qui sont des demandes de portage sont marquées avec l’étiquette [port-à-core.](https://github.com/dotnet/runtime/labels/port-to-core)

## <a name="appdomains"></a>AppDomains

Les domaines d’application (AppDomains) isolent les applications les unes des autres. Ils requièrent la prise en charge du runtime et sont généralement assez onéreux. La création de domaines d’applications supplémentaires n’est pas prise en charge, et il n’est pas prévu d’ajouter cette capacité à l’avenir. Pour l’isolement du code, utilisez des processus ou des conteneurs distincts comme solution de rechange. Pour charger dynamiquement les <xref:System.Runtime.Loader.AssemblyLoadContext> assemblages, utilisez la classe.

Pour faciliter la migration de code à partir du .NET Framework, .NET Core expose une partie de la surface d’API <xref:System.AppDomain>. Certaines API fonctionnent normalement (par exemple, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), certains membres ne font rien (par exemple, <xref:System.AppDomain.SetCachePath%2A>) et d’autres lèvent <xref:System.PlatformNotSupportedException> (par exemple, <xref:System.AppDomain.CreateDomain%2A>). Vérifiez les types que [ `System.AppDomain` ](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) vous utilisez par rapport à la source de référence dans le [référentiel GitHub pointnet/runtime](https://github.com/dotnet/runtime). Assurez-vous de sélectionner la branche qui correspond à votre version mise en œuvre.

## <a name="remoting"></a>Communication à distance

.NET Remoting a été identifié comme architecture problématique. Elle est utilisée pour la communication entre AppDomains, qui n’est plus prise en charge. Par ailleurs, Remoting requiert la prise en charge du runtime, dont la maintenance est coûteuse. C’est pourquoi .NET Remoting n’est pas pris en charge sur .NET Core, et nous ne prévoyons pas d’ajouter sa prise en charge à l’avenir.

Pour la communication entre les processus, considérez les mécanismes de communication interprofessionnelle (IPC) comme une alternative à la refonte, comme la <xref:System.IO.Pipes> classe ou la <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> classe.

Pour la communication entre ordinateurs, utilisez plutôt une solution réseau. Choisissez de préférence un protocole de texte brut à faible charge, par exemple HTTP. Le [serveur web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), utilisé par ASP.NET Core, est une possibilité. En outre, <xref:System.Net.Sockets> envisager d’utiliser pour le réseau, les scénarios multi-machines. Pour plus d’options, consultez la page [Projets de développement .NET open source : messagerie](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Sécurité d'accès du code

Le sandboxing, qui s’appuie sur le runtime ou le framework pour limiter les ressources utilisées ou exécutées par une application gérée ou une bibliothèque, [n’est pas pris en charge sur .NET Framework](../../framework/misc/code-access-security.md) ni, par conséquent, sur .NET Core. Les cas sont trop nombreux dans .NET Framework et le runtime où une élévation des privilèges se produit pour continuer à considérer la sécurité d’accès du code comme une limite de sécurité. En outre, la sécurité du code complique l’implémentation et a souvent a des implications en matière de performances d’exactitude pour les applications qui ne prévoient pas de l’utiliser.

Utilisez les limites de sécurité fournies par le système d’exploitation, tels que la virtualisation, les conteneurs ou les comptes d’utilisateurs, pour l’exécution de processus avec l’ensemble minimum de privilèges.

## <a name="security-transparency"></a>Transparence de la sécurité

Tout comme la sécurité d’accès du code, la transparence de la sécurité sépare le code sandbox du code critique de sécurité d’une manière déclarative, mais [n’est plus prise en charge en tant que limite de sécurité](../../framework/misc/security-transparent-code.md). Cette fonctionnalité est très utilisée par Silverlight.

Utilisez les limites de sécurité fournies par le système d’exploitation, tels que la virtualisation, les conteneurs ou les comptes d’utilisateurs, pour l’exécution de processus avec le moins de privilèges.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

System.EnterpriseServices (COM+) n’est pas pris en charge par .NET Core.

## <a name="see-also"></a>Voir aussi

- [Aperçu du portage du cadre .NET à .NET Core](../porting/index.md)
