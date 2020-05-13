---
title: Noms d’assembly
description: En savoir plus sur les noms d’assemblys .NET et leur impact sur la portée de l’assembly et leur utilisation par une application, et en savoir plus sur la propriété FullName.
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 5a499f4f04c84de8d6542d7107d7a707b808e47f
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379888"
---
# <a name="assembly-names"></a>Noms d’assembly
Le nom d’un assembly est stocké dans des métadonnées, et il a un impact significatif sur l’étendue de l’assembly et sur son utilisation dans une application. Un assembly avec nom fort a un nom qualifié complet qui inclut le nom, la culture, la clé publique et le numéro de version de l’assembly. Ceci est fréquemment appelé le nom d’affichage et, pour les assemblys chargés, il peut être obtenu avec la propriété <xref:System.Reflection.Assembly.FullName%2A>.

 Le runtime utilise ces informations pour localiser l’assembly et pour le différencier des autres assemblys portant le même nom. Par exemple, un assembly avec un nom fort appelé `myTypes` peut avoir le nom qualifié complet suivant :

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> Une architecture de processeur est ajoutée à l’identité de l’assembly dans le .NET Framework version 2.0, pour permettre des versions d’assemblys spécifiques au processeur. Vous pouvez créer des versions d’un assembly dont l’identité diffère seulement par l’architecture de processeur, par exemple des versions spécifiques à des processeurs 32 bits et 64 bits. L’architecture de processeur n’est pas obligatoire pour les noms forts. Pour plus d'informations, consultez <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 Dans cet exemple, le nom qualifié complet indique que l’assembly `myTypes` a un nom fort avec un jeton de clé publique, a comme valeur Anglais (États-Unis) pour la culture et a comme numéro de version 1.0.1234.0. Son architecture de processeur est « msil », ce qui signifie qu’il sera compilé juste-à-temps (JIT)-compilé en code 32 bits ou 64 bits, en fonction du système d’exploitation et du processeur.

 Le code qui demande des types dans un assembly doit utiliser un nom d’assembly qualifié complet. Ceci s’appelle une liaison qualifiée complète. Une liaison partielle, qui spécifie seulement un nom d’assembly, n’est pas autorisée lors du référencement d’assemblys dans le .NET Framework.

 Toutes les références d’assembly aux assemblys qui composent le .NET Framework doivent également contenir le nom qualifié complet de l’assembly. Par exemple, une référence à l’assembly System. Data .NET Framework pour la version 1,0 inclut les éléments suivants :

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

 Notez que la version correspond au numéro de version de tous les assemblys .NET Framework fournis avec le .NET Framework version 1.0. Pour les assemblys .NET Framework, la valeur de culture est toujours neutre, et la clé publique est identique à celle qui est montrée dans l’exemple ci-dessus.

 Par exemple, pour ajouter une référence d’assembly dans un fichier de configuration pour configurer un écouteur de suivi, vous incluez le nom qualifié complet de l’assembly system de .NET Framework :

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> Le runtime traite les noms d’assemblys sans tenir compte de la casse lors de la liaison à un assembly, mais il conserve la casse utilisée dans un nom d’assembly. Plusieurs outils du SDK Windows gèrent les noms d’assembly en respectant la casse. Pour de meilleurs résultats, gérez les noms d’assemblys comme s’ils tenaient compte de la casse.

## <a name="name-application-components"></a>Nommer les composants de l’application
 Le runtime ne prend pas en compte pas le nom de fichier pour déterminer l’identité d’un assembly. L’identité de l’assembly, qui est constituée du nom, de la version, de la culture et du nom fort de l’assembly, doit être claire pour le runtime.

 Par exemple, si vous avez un assembly appelé *myAssembly. exe* qui référence un assembly appelé *myAssembly. dll*, la liaison se produit correctement si vous exécutez *myAssembly. exe*. Toutefois, si une autre application exécute *myAssembly. exe* à l’aide de la méthode <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> , le runtime détermine que `myAssembly` est déjà chargé lorsque *myAssembly. exe* demande une liaison à `myAssembly` . Dans ce cas, *myAssembly. dll* n’est jamais chargé. Étant donné que *myAssembly. exe* ne contient pas le type demandé, une <xref:System.TypeLoadException> se produit.

 Pour éviter ce problème, vérifiez que les assemblys qui composent votre application n’ont pas le même nom d’assembly ou que vous placez les assemblys portant le même nom dans des répertoires différents.

> [!NOTE]
> Dans le .NET Framework, si vous placez un assembly avec nom fort dans le Global Assembly Cache, le nom de fichier de l’assembly doit correspondre au nom de l’assembly, sans l’extension de nom de fichier, par exemple *. exe* ou *. dll*. Par exemple, si le nom de fichier d’un assembly est *myAssembly. dll*, le nom de l’assembly doit être `myAssembly` . Les assemblys privés déployés uniquement dans le répertoire racine de l’application peuvent avoir un nom d’assembly différent du nom du fichier.

## <a name="see-also"></a>Voir aussi

- [Comment : déterminer le nom qualifié complet d’un assembly](find-fully-qualified-name.md)
- [Créer des assemblys](create.md)
- [Assemblys avec nom fort](strong-named.md)
- [Global assembly cache](../../framework/app-domains/gac.md)
- [Comment le runtime localise les assemblys](../../framework/deployment/how-the-runtime-locates-assemblies.md)
