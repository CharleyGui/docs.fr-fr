---
title: 'Procédure : Créer une stratégie d’éditeur'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646053"
---
# <a name="how-to-create-a-publisher-policy"></a>Procédure : Créer une stratégie d’éditeur

Les fournisseurs d’assemblys peuvent indiquer que les applications doivent utiliser une version plus récente d’un assembly en incluant un fichier de stratégie d’éditeur avec l’assembly mis à niveau. Le fichier de stratégie d’éditeur spécifie la redirection d’assembly et les paramètres de base de code, et utilise le même format qu’un fichier de configuration d’application. Le fichier de stratégie d’éditeur est compilé dans un assembly et placé dans le Global Assembly Cache.

La création d’une stratégie d’éditeur implique trois étapes :

1. Créez un fichier de stratégie d’éditeur.

2. Créer un assembly de stratégie d’éditeur.

3. Ajoutez l’assembly de stratégie d’éditeur au Global Assembly Cache.

Le schéma de la stratégie d’éditeur est décrit dans [redirection des versions d’assembly](redirect-assembly-versions.md). L’exemple suivant montre un fichier de stratégie d’éditeur qui redirige une version de `myAssembly` vers une autre.

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

Pour savoir comment spécifier une base de code, consultez [spécification de l’emplacement d’un assembly](specify-assembly-location.md).

## <a name="creating-the-publisher-policy-assembly"></a>Création de l’assembly de stratégie d’éditeur

Utilisez [Assembly Linker (al. exe)](../tools/al-exe-assembly-linker.md) pour créer l’assembly de stratégie d’éditeur.

#### <a name="to-create-a-publisher-policy-assembly"></a>Pour créer un assembly de stratégie d’éditeur

Entrez la commande suivante à l'invite de commandes :

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

Dans cette commande :

- L' `publisherPolicyFile` argument est le nom du fichier de stratégie d’éditeur.

- L' `publisherPolicyAssemblyFile` argument est le nom de l’assembly de stratégie d’éditeur qui résulte de cette commande. Le nom du fichier de l’assembly doit respecter le format suivant :

  'Policy. majorNumber. minorNumber. mainAssemblyName. dll'

- L' `keyPairFile` argument est le nom du fichier contenant la paire de clés. Vous devez signer l’assembly et l’assembly de stratégie d’éditeur avec la même paire de clés.

- L' `processorArchitecture` argument identifie la plateforme ciblée par un assembly spécifique au processeur.

  > [!NOTE]
  > La possibilité de cibler une architecture de processeur spécifique est disponible à partir de .NET Framework 2,0.

La possibilité de cibler une architecture de processeur spécifique est disponible à partir de .NET Framework 2,0. La commande suivante crée un assembly de stratégie `policy.1.0.myAssembly` d’éditeur appelé à partir d’un fichier de stratégie d’éditeur appelé `pub.config` , attribue un nom fort à l’assembly à l’aide de la paire de clés dans le `sgKey.snk` fichier et spécifie que l’assembly cible l’architecture de processeur x86.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

L’assembly de stratégie d’éditeur doit correspondre à l’architecture de processeur de l’assembly auquel il s’applique. Ainsi, si votre assembly a la <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> valeur <xref:System.Reflection.ProcessorArchitecture.MSIL> , l’assembly de stratégie d’éditeur de cet assembly doit être créé avec `/platform:anycpu` . Vous devez fournir un assembly de stratégie d’éditeur distinct pour chaque assembly spécifique au processeur.

Une conséquence de cette règle est que pour modifier l’architecture de processeur d’un assembly, vous devez modifier le composant principal ou mineur du numéro de version, afin de pouvoir fournir un nouvel assembly de stratégie d’éditeur avec l’architecture de processeur correcte. L’ancien assembly de stratégie d’éditeur ne peut pas traiter votre assembly une fois que votre assembly a une architecture de processeur différente.

Une autre conséquence est que l’éditeur de liens version 2,0 ne peut pas être utilisé pour créer un assembly de stratégie d’éditeur pour un assembly compilé à l’aide de versions antérieures du .NET Framework, car il spécifie toujours l’architecture du processeur.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Ajout de l’assembly de stratégie d’éditeur au global assembly cache

Utilisez l' [outil global assembly cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter l’assembly de stratégie d’éditeur au global assembly cache.

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Pour ajouter l’assembly de stratégie d’éditeur au Global Assembly Cache

Entrez la commande suivante à l'invite de commandes :

```console
gacutil /i publisherPolicyAssemblyFile
```

La commande suivante ajoute `policy.1.0.myAssembly.dll` à la global assembly cache.

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> L’assembly de stratégie d’éditeur ne peut pas être ajouté au Global Assembly Cache, sauf si le fichier de stratégie d’éditeur d’origine spécifié dans l' `/link` argument se trouve dans le même répertoire que l’assembly.

## <a name="see-also"></a>Voir aussi

- [Programmation à l’aide d’assemblys](../../standard/assembly/index.md)
- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Configuration des applications à l'aide de fichiers de configuration](index.md)
- [Schéma des paramètres d’exécution](./file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](./file-schema/index.md)
- [Redirection des versions d'assemblys](redirect-assembly-versions.md)
