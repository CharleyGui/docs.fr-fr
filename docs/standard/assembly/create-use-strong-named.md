---
title: Créer et utiliser des assemblys avec nom fort
ms.date: 08/19/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
ms.openlocfilehash: 18a0b7d657290835a34c705513d0d7a4ccbfc61c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75738680"
---
# <a name="create-and-use-strong-named-assemblies"></a>Créer et utiliser des assemblys avec nom fort

Un nom fort est constitué de l'identité de l'assembly (son simple nom textuel, son numéro de version et des informations de culture, le cas échéant) ainsi que d'une clé publique et d'une signature numérique. Il est généré à partir d'un fichier d'assembly à l'aide de la clé privée correspondante. (Le fichier d'assembly contient le manifeste d'assembly, qui contient les noms et les hachages de tous les fichiers composant l'assembly.)

> [!WARNING]
> Ne comptez pas sur les noms forts pour la sécurité. Ils fournissent seulement une identité unique.

Un assembly avec nom fort peut uniquement utiliser les types d'autres assemblys avec nom fort. Si ce n'était pas le cas, l’intégrité de l’assembly avec nom fort serait compromise.

> [!NOTE]
> Bien que .NET Core soutienne des assemblées de nom fort, et que toutes les assemblées de la bibliothèque .NET Core soient signées, la majorité des assemblées tierces n’ont pas besoin de noms forts. Pour plus d’informations, voir [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) sur GitHub.

## <a name="strong-name-scenario"></a>Scénario de nom fort

Le scénario suivant met en avant le processus de signature d'un assembly avec nom fort, puis son référencement par ce nom.

1. L'assembly A est créé avec un nom fort à l'aide de l'une des méthodes suivantes :

    - En utilisant un environnement de développement qui prend en charge la création de noms forts, tel que Visual Studio.

    - En créant une paire de clés de chiffrement avec l’[outil Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) et en l’assignant à l’assembly à l’aide d’un compilateur de ligne de commande ou de [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md). Le SDK Windows fournit Sn.exe et Al.exe.

2. L'environnement de développement ou l'outil signe le hachage du fichier contenant le manifeste de l'assembly avec la clé privée du développeur. Cette signature numérique est stockée dans le fichier exécutable portable (PE) qui contient le manifeste de l'assembly A.

3. L’assembly B est un consommateur de l’Assembly A. La section de référence du manifeste de l’assembly B inclut un jeton qui représente la clé publique de l’assembly A. Un jeton est une partie de la clé publique complète. Il est utilisé à la place de la clé pour économiser de l'espace.

4. Le Common Language Runtime vérifie la signature de nom fort quand l'assembly est placé dans le Global Assembly Cache. Lors de la liaison par nom fort au moment de l’exécution, le common language runtime compare la clé stockée dans le manifeste de l’Assembly B avec la clé utilisée pour générer le nom fort de l’Assembly A. Si les vérifications de la sécurité .NET Framework et la liaison réussissent, l’Assembly B a une garantie que les bits de l’Assembly A n’ont pas été falsifiés et qu’ils proviennent réellement des développeurs de l’Assembly A.

> [!NOTE]
> Ce scénario ne traite pas des problèmes de confiance. Outre un nom fort, les assemblys peuvent posséder des signatures Microsoft Authenticode complètes. Les signatures Authenticode incluent un certificat établissant la confiance. Il est important de noter que les noms forts ne nécessitent pas que le code soit signé de cette manière. Les noms forts fournissent seulement une identité unique.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Ignorer la vérification de signature des assemblys approuvés

À partir du .NET Framework 3.5 Service Pack 1, les signatures de nom fort ne sont pas validées quand un assembly est chargé dans un domaine d'application de confiance totale tel que le domaine de l'application par défaut pour la zone `MyComputer`. Cette fonctionnalité permet d’ignorer les noms forts. Dans un environnement de confiance totale, les demandes de <xref:System.Security.Permissions.StrongNameIdentityPermission> aboutissent toujours pour les assemblys de confiance totale signés, quelle que soit leur signature. La fonctionnalité consistant à ignorer les noms forts évite les traitements inutiles liés à la vérification de signature de nom fort des assemblys de confiance totale dans cette situation, ce qui permet un chargement plus rapide des assemblys.

Cette fonctionnalité s’applique à tout assembly signé avec un nom fort qui présente les caractéristiques suivantes :

- Confiance totale sans preuve <xref:System.Security.Policy.StrongName> (par exemple, dispose de la preuve de zone `MyComputer`).

- Chargé dans un <xref:System.AppDomain> de confiance totale.

- Chargé à partir d'un emplacement sous la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> de cet <xref:System.AppDomain>.

- Sans signature différée.

Cette fonctionnalité peut être désactivée pour des applications individuelles ou pour un ordinateur. Voir [comment : Désactiver la fonction de contournement de nom fort](disable-strong-name-bypass-feature.md).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Guide pratique pour créer une paire de clés publique/privée](create-public-private-key-pair.md)|Décrit comment créer une paire de clés de chiffrement pour signer un assembly.|
|[Comment: Signer une assemblée avec un nom fort](sign-strong-name.md)|Décrit comment créer un assembly avec nom fort.|
|[Amélioration de l’utilisation de noms forts](enhanced-strong-naming.md)|Décrit les améliorations apportées aux noms forts dans .NET Framework 4.5.|
|[Comment : Référencez une assemblée forte](reference-strong-named.md)|Décrit comment référencer des types ou des ressources dans un assembly avec nom fort au moment de la compilation ou de l'exécution.|
|[Comment : Désactiver la fonction de contournement de nom fort](disable-strong-name-bypass-feature.md)|Décrit comment désactiver la fonctionnalité qui ignore la validation des signatures avec nom fort. Cette fonctionnalité peut être désactivée pour toutes les applications ou pour des applications spécifiques.|
|[Créer des assemblys](create.md)|Fournit une vue d'ensemble des assemblys multifichiers et à fichier unique.|
|[Comment retarder la signature d’un assemblage dans Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Explique comment signer un assembly avec un nom fort après la création de l'assembly.|
|[Sn.exe (outil Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md)|Décrit l'outil inclus dans le .NET Framework qui facilite la création d'assemblys avec des noms forts. Cet outil fournit des options de gestion des clés, de génération des signatures et de vérification des signatures.|
|[Al.exe (Lien de l’Assemblée)](../../framework/tools/al-exe-assembly-linker.md)|Décrit l'outil inclus dans le .NET Framework qui génère un fichier possédant un manifeste d'assembly à partir de modules ou de fichiers de ressources.|
