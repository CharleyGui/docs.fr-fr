---
title: .NET Framework technologies non disponibles sur .NET Core et .NET 5 +
titleSuffix: ''
description: En savoir plus sur les technologies .NET Framework qui ne sont pas disponibles sur .NET Core et .NET 5,0 et versions ultérieures.
author: cartermp
ms.date: 01/26/2021
ms.openlocfilehash: d5926d2c0cfe6d2073ac6ad74046ca48b9cb18f1
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898773"
---
# <a name="net-framework-technologies-unavailable-on-net-core-and-net-5"></a>.NET Framework technologies non disponibles sur .NET Core et .NET 5 +

Plusieurs technologies disponibles pour .NET Framework bibliothèques ne peuvent pas être utilisées avec .NET Core et .NET 5,0 et versions ultérieures, telles que les domaines d’application, la communication à distance et la sécurité d’accès du code (CAS). Si vos bibliothèques reposent sur une ou plusieurs des technologies répertoriées sur cette page, tenez compte des autres approches mentionnées.

Pour plus d’informations sur la compatibilité des API, consultez [modifications avec rupture dans .net](../compatibility/breaking-changes.md).

## <a name="application-domains"></a>Domaines d'application

Les domaines d’application (AppDomains) isolent les applications les unes des autres. Les AppDomains nécessitent une prise en charge du runtime et sont généralement coûteux. La création de domaines d’application supplémentaires n’est pas prise en charge et il n’est pas prévu d’ajouter cette fonctionnalité à l’avenir. Pour l’isolation du code, utilisez des processus ou des conteneurs séparés comme alternative. Pour charger dynamiquement des assemblys, utilisez la <xref:System.Runtime.Loader.AssemblyLoadContext> classe.

Pour faciliter la migration du code .NET Framework, .NET 5 + expose une partie de la surface de l' <xref:System.AppDomain> API. Certaines API fonctionnent normalement (par exemple, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), certains membres ne font rien (par exemple, <xref:System.AppDomain.SetCachePath%2A>) et d’autres lèvent <xref:System.PlatformNotSupportedException> (par exemple, <xref:System.AppDomain.CreateDomain%2A>). Vérifiez les types que vous utilisez par rapport à la [ `System.AppDomain` source de référence](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) dans le [référentiel GitHub dotnet/Runtime](https://github.com/dotnet/runtime). Veillez à sélectionner la branche qui correspond à votre version implémentée.

## <a name="remoting"></a>Communication à distance

.NET Remoting a été identifié comme une architecture problématique. Il est utilisé pour la communication entre des domaines d’application qui ne sont plus pris en charge. En outre, la communication à distance nécessite une prise en charge du runtime, dont la maintenance est coûteuse. Pour ces raisons, .NET Remoting n’est pas pris en charge sur .NET Core et .NET 5 +, et nous ne prévoyons pas d’ajouter la prise en charge à l’avenir.

Pour la communication entre les processus, envisagez les mécanismes de communication entre processus (IPC) comme une alternative à la communication à distance, telle que la <xref:System.IO.Pipes> classe ou <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> .

Pour la communication entre ordinateurs, utilisez plutôt une solution réseau. Choisissez de préférence un protocole de texte brut à faible charge, par exemple HTTP. Le [serveur Web Kestrel](/aspnet/core/fundamentals/servers/kestrel), qui est le serveur Web utilisé par ASP.net Core, est une option ici. Envisagez également <xref:System.Net.Sockets> d’utiliser pour les scénarios sur plusieurs ordinateurs basés sur le réseau. Pour plus d’options, consultez la page [Projets de développement .NET open source : messagerie](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Sécurité d’accès du code (CAS)

Le sandboxing, qui repose sur le runtime ou l’infrastructure pour contraindre les ressources qu’une application ou une bibliothèque managée utilise ou exécute, n’est pas [pris en charge sur les .NET Framework](../../framework/misc/code-access-security.md) et n’est donc pas pris en charge sur .net Core et .net 5 +. Les cas sont trop nombreux dans .NET Framework et le runtime où une élévation des privilèges se produit pour continuer à considérer la sécurité d’accès du code comme une limite de sécurité. En outre, la sécurité du code complique l’implémentation et a souvent a des implications en matière de performances d’exactitude pour les applications qui ne prévoient pas de l’utiliser.

Utilisez les limites de sécurité fournies par le système d’exploitation, telles que la virtualisation, les conteneurs ou les comptes d’utilisateur, pour l’exécution des processus avec l’ensemble minimal de privilèges.

## <a name="security-transparency"></a>Transparence de la sécurité

Comme pour les autorités de certification, la transparence de la sécurité sépare le code sandbox du code critique de sécurité de façon déclarative, mais n’est [plus pris en charge comme limite de sécurité](../../framework/misc/security-transparent-code.md). Cette fonctionnalité est très utilisée par Silverlight.

Utilisez les limites de sécurité fournies par le système d’exploitation, telles que la virtualisation, les conteneurs ou les comptes d’utilisateur, pour l’exécution de processus avec le plus petit ensemble de privilèges.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

<xref:System.EnterpriseServices?displayProperty=fullName> (COM+) n’est pas pris en charge par .NET Core et .NET 5 +.

## <a name="workflow-foundation-and-wcf"></a>Workflow Foundation et WCF

Windows Workflow Foundation (WF) et Windows Communication Foundation (WCF) ne sont pas pris en charge dans .NET 5 + (y compris .NET Core). Pour les autres solutions, consultez [CoreWF](https://github.com/UiPath/corewf) et [CoreWCF](https://github.com/CoreWCF/CoreWCF).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du Portage à partir de .NET Framework vers .NET Core](index.md)
