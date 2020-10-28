---
title: Noms d’assembly
description: En savoir plus sur les noms d’assemblys .NET et leur impact sur la portée de l’assembly et leur utilisation par une application, et en savoir plus sur la propriété FullName.
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET], assemblies
- assemblies [.NET], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 136c3b7a06ce72be02e00bcc4d2354160178468c
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687574"
---
# <a name="assembly-names"></a>Noms d’assembly

Le nom d’un assembly est stocké dans des métadonnées, et il a un impact significatif sur l’étendue de l’assembly et sur son utilisation dans une application. Un assembly avec nom fort possède un nom qualifié complet qui inclut le nom de l’assembly, la culture, la clé publique, le numéro de version et, éventuellement, l’architecture du processeur. Utilisez la <xref:System.Reflection.Assembly.FullName%2A> propriété pour obtenir le nom complet, souvent appelé nom d’affichage, pour les assemblys chargés.

Le runtime utilise les informations de nom pour Rechercher l’assembly et le différencier des autres assemblys portant le même nom. Par exemple, un assembly avec un nom fort appelé `myTypes` peut avoir le nom qualifié complet suivant :

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

Dans cet exemple, le nom complet indique que l' `myTypes` assembly a un nom fort avec un jeton de clé publique, a la valeur de culture pour États-Unis anglais et a un numéro de version de 1.0.1234.0. Son architecture de processeur est, ce qui `msil` signifie qu’elle sera compilée juste-à-temps (JIT) en code 32 bits ou en code 64 bits en fonction du système d’exploitation et du processeur.

> [!TIP]
> Les `ProcessorArchitecture` informations autorisent les versions spécifiques au processeur des assemblys. Vous pouvez créer des versions d’un assembly dont l’identité diffère seulement par l’architecture de processeur, par exemple des versions spécifiques à des processeurs 32 bits et 64 bits. L’architecture de processeur n’est pas obligatoire pour les noms forts. Pour plus d'informations, consultez <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 Le code qui demande des types dans un assembly doit utiliser un nom d’assembly qualifié complet. Ceci s’appelle une liaison qualifiée complète. La liaison partielle, qui spécifie uniquement un nom d’assembly, n’est pas autorisée lors du référencement d’assemblys dans .NET Framework.

 Toutes les références d’assembly aux assemblys qui composent .NET Framework doivent également contenir le nom qualifié complet de l’assembly. Par exemple, une référence à l’assembly System. Data .NET Framework pour la version 1,0 inclut les éléments suivants :

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

La version correspond au numéro de version de tous les assemblys .NET Framework fournis avec .NET Framework version 1,0. Pour les assemblys .NET Framework, la valeur de culture est toujours neutre, et la clé publique est identique à celle qui est montrée dans l’exemple ci-dessus.

 Par exemple, pour ajouter une référence d’assembly dans un fichier de configuration pour configurer un écouteur de suivi, vous incluez le nom qualifié complet de l’assembly system de .NET Framework :

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> Le runtime traite les noms d’assemblys sans tenir compte de la casse lors de la liaison à un assembly, mais il conserve la casse utilisée dans un nom d’assembly. Plusieurs outils du SDK Windows gèrent les noms d’assembly en respectant la casse. Pour de meilleurs résultats, gérez les noms d’assemblys comme s’ils tenaient compte de la casse.

## <a name="name-application-components"></a>Nommer les composants de l’application
 Le runtime ne prend pas en compte pas le nom de fichier pour déterminer l’identité d’un assembly. L’identité de l’assembly, qui est constituée du nom, de la version, de la culture et du nom fort de l’assembly, doit être claire pour le runtime.

 Par exemple, si vous avez un assembly appelé *myAssembly.exe* qui fait référence à un assembly appelé *myAssembly.dll* , la liaison s’effectue correctement si vous exécutez *myAssembly.exe* . Toutefois, si une autre application exécute *myAssembly.exe* à l’aide de la méthode <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> , le runtime détermine que `myAssembly` est déjà chargé lorsque *myAssembly.exe* demande la liaison à `myAssembly` . Dans ce cas, *myAssembly.dll* n’est jamais chargé. Étant donné que *myAssembly.exe* ne contient pas le type demandé, une <xref:System.TypeLoadException> se produit.

 Pour éviter ce problème, vérifiez que les assemblys qui composent votre application n’ont pas le même nom d’assembly ou que vous placez les assemblys portant le même nom dans des répertoires différents.

> [!NOTE]
> Dans .NET Framework, si vous placez un assembly avec nom fort dans le Global Assembly Cache, le nom de fichier de l’assembly doit correspondre au nom de l’assembly, à l’exclusion de l’extension de nom de fichier, par exemple *. exe* ou *. dll* . Par exemple, si le nom de fichier d’un assembly est *myAssembly.dll* , le nom de l’assembly doit être `myAssembly` . Les assemblys privés déployés uniquement dans le répertoire racine de l’application peuvent avoir un nom d’assembly différent du nom du fichier.

## <a name="see-also"></a>Voir aussi

- [Comment : déterminer le nom qualifié complet d’un assembly](find-fully-qualified-name.md)
- [Créer des assemblys](create.md)
- [Assemblys avec nom fort](strong-named.md)
- [Global assembly cache](../../framework/app-domains/gac.md)
- [Comment le runtime localise les assemblys](../../framework/deployment/how-the-runtime-locates-assemblies.md)
