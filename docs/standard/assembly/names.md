---
title: Noms d’assembly
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 7a1a4d2512ebb002a3153fe2d51f47157136744d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733101"
---
# <a name="assembly-names"></a>Noms d’assembly
Le nom d’un assembly est stocké dans des métadonnées, et il a un impact significatif sur l’étendue de l’assembly et sur son utilisation dans une application. Un assembly avec nom fort a un nom qualifié complet qui inclut le nom, la culture, la clé publique et le numéro de version de l’assembly. Ceci est fréquemment appelé le nom d’affichage et, pour les assemblys chargés, il peut être obtenu avec la propriété <xref:System.Reflection.Assembly.FullName%2A>.

 Le runtime utilise ces informations pour localiser l’assembly et pour le différencier des autres assemblys portant le même nom. Par exemple, un assembly avec un nom fort appelé `myTypes` peut avoir le nom qualifié complet suivant :

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> Une architecture de processeur est ajoutée à l’identité de l’assembly dans le .NET Framework version 2.0, pour permettre des versions d’assemblys spécifiques au processeur. Vous pouvez créer des versions d’un assembly dont l’identité diffère seulement par l’architecture de processeur, par exemple des versions spécifiques à des processeurs 32 bits et 64 bits. L’architecture de processeur n’est pas obligatoire pour les noms forts. Pour plus d’informations, consultez <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 Dans cet exemple, le nom qualifié complet indique que l’assembly `myTypes` a un nom fort avec un jeton de clé publique, a comme valeur Anglais (États-Unis) pour la culture et a comme numéro de version 1.0.1234.0. Son architecture de processeur est « msil », ce qui signifie qu’il sera compilé juste-à-temps (JIT)-compilé en code 32 bits ou 64 bits, en fonction du système d’exploitation et du processeur.

 Le code qui demande des types dans un assembly doit utiliser un nom d’assembly qualifié complet. Ceci s’appelle une liaison qualifiée complète. Une liaison partielle, qui spécifie seulement un nom d’assembly, n’est pas autorisée lors du référencement d’assemblys dans le .NET Framework.

 Toutes les références d’assemblage aux assemblées qui composent le cadre .NET doivent également contenir le nom entièrement qualifié de l’assemblée. Par exemple, une référence à l’assemblage cadre System.Data .NET pour la version 1.0 comprendrait :

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

## <a name="name-application-components"></a>Nom des composants d’application
 Le runtime ne prend pas en compte pas le nom de fichier pour déterminer l’identité d’un assembly. L’identité de l’assembly, qui est constituée du nom, de la version, de la culture et du nom fort de l’assembly, doit être claire pour le runtime.

 Par exemple, si vous avez une assemblée appelée *myAssembly.exe* qui fait référence à une assemblée appelée *myAssembly.dll*, la liaison se produit correctement si vous exécutez *myAssembly.exe*. Cependant, si une autre application exécute *myAssembly.exe* en <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>utilisant `myAssembly` la méthode , le temps d’exécution détermine qui est déjà chargé lorsque *myAssembly.exe* demandes de liaison à `myAssembly`. Dans ce cas, *myAssembly.dll n’est* jamais chargé. Parce que *myAssembly.exe* ne contient <xref:System.TypeLoadException> pas le type demandé, un se produit.

 Pour éviter ce problème, vérifiez que les assemblys qui composent votre application n’ont pas le même nom d’assembly ou que vous placez les assemblys portant le même nom dans des répertoires différents.

> [!NOTE]
> Dans le cadre .NET, si vous mettez une assemblée forte nommée dans le cache de l’assemblée mondiale, le nom de fichier de l’assemblée doit correspondre au nom de l’assemblée, sans compter l’extension du nom de fichier, tels que *.exe* ou *.dll*. Par exemple, si le nom de fichier d’une assemblée est *myAssembly.dll*, le nom de l’assemblée doit être `myAssembly`. Les assemblys privés déployés uniquement dans le répertoire racine de l’application peuvent avoir un nom d’assembly différent du nom du fichier.

## <a name="see-also"></a>Voir aussi

- [Comment : Déterminer le nom entièrement qualifié d’une assemblée](find-fully-qualified-name.md)
- [Créer des assemblys](create.md)
- [Assemblées de bien-être](strong-named.md)
- [Cache d’assemblage global](../../framework/app-domains/gac.md)
- [Comment le temps d’exécution localise les assemblages](../../framework/deployment/how-the-runtime-locates-assemblies.md)
