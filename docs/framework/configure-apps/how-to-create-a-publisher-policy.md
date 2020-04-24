---
title: "Comment : créer une stratégie d'éditeur"
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646053"
---
# <a name="how-to-create-a-publisher-policy"></a>Comment : créer une stratégie d'éditeur

Les fournisseurs d’assemblages peuvent indiquer que les applications doivent utiliser une version plus récente d’un assemblage en incluant un fichier de politique d’éditeur avec l’assemblage mis à niveau. Le fichier de politique de l’éditeur spécifie les paramètres de réorientation d’assemblage et de base de code, et utilise le même format qu’un fichier de configuration d’application. Le fichier de politique de l’éditeur est compilé dans une assemblée et placé dans le cache d’assemblage global.

La création d’une politique d’éditeur comporte trois étapes :

1. Créez un fichier de politique d’éditeur.

2. Créer une assemblée des politiques de l’éditeur.

3. Ajoutez l’assemblage de la politique de l’éditeur au cache d’assemblage global.

Le schéma de la politique de l’éditeur est décrit dans [Redirecting Assembly Versions](redirect-assembly-versions.md). L’exemple suivant montre un fichier de `myAssembly` politique d’éditeur qui redirige une version d’une autre.

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

Pour savoir comment spécifier une base de code, voir [spécifier l’emplacement d’une Assemblée](specify-assembly-location.md).

## <a name="creating-the-publisher-policy-assembly"></a>Création de l’Assemblée des politiques des éditeurs

Utilisez le [Linker de l’Assemblée (Al.exe)](../tools/al-exe-assembly-linker.md) pour créer l’assemblée des politiques de l’éditeur.

#### <a name="to-create-a-publisher-policy-assembly"></a>Créer une assemblée des politiques de l’éditeur

Entrez la commande suivante à l'invite de commandes :

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

Dans cette commande :

- L’argument `publisherPolicyFile` est le nom du dossier de politique de l’éditeur.

- L’argument `publisherPolicyAssemblyFile` est le nom de l’assemblée des politiques de l’éditeur qui résulte de cette commande. Le nom du fichier d’assemblage doit suivre le format :

  'policy.majorNumber.minorNumber.mainAssemblyName.dll'

- L’argument `keyPairFile` est le nom du fichier contenant la paire de clés. Vous devez signer l’assemblage et l’assemblage des politiques de l’éditeur avec la même paire clé.

- L’argument `processorArchitecture` identifie la plate-forme ciblée par un assemblage spécifique au processeur.

  > [!NOTE]
  > La possibilité de cibler une architecture de processeur spécifique est disponible à partir de .NET Framework 2.0.

La possibilité de cibler une architecture de processeur spécifique est disponible à partir de .NET Framework 2.0. La commande suivante crée un `policy.1.0.myAssembly` assemblage de politique `pub.config`d’éditeur appelé à partir d’un `sgKey.snk` fichier de politique d’éditeur appelé , attribue un nom fort à l’assemblage en utilisant la paire de clés dans le fichier, et précise que l’assemblage cible l’architecture du processeur x86.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

L’assemblage de la politique de l’éditeur doit correspondre à l’architecture de processeur de l’assemblage à laquelle il s’applique. Ainsi, si votre <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> assemblée <xref:System.Reflection.ProcessorArchitecture.MSIL>a une valeur de , l’assemblage de la politique de l’éditeur pour cette assemblée doit être créé avec `/platform:anycpu`. Vous devez fournir un assemblage distinct de la politique de l’éditeur pour chaque assemblage spécifique au processeur.

Une conséquence de cette règle est que pour changer l’architecture du processeur pour un assemblage, vous devez modifier la composante majeure ou mineure du numéro de version, de sorte que vous pouvez fournir un nouvel assemblage de politique d’éditeur avec l’architecture de processeur correcte. L’ancien assemblage de la politique de l’éditeur ne peut pas servir votre assemblage une fois que votre assemblage a une architecture de processeur différente.

Une autre conséquence est que la version 2.0 linker ne peut pas être utilisé pour créer un assemblage de politique d’éditeur pour une assemblée compilée en utilisant des versions antérieures du cadre .NET, car il spécifie toujours l’architecture du processeur.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Ajout de l’Assemblée des politiques des éditeurs au Cache de l’Assemblée mondiale

Utilisez [l’outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter l’assemblage des politiques de l’éditeur au cache d’assemblage mondial.

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Pour ajouter l’assemblage de la politique de l’éditeur au cache d’assemblage mondial

Entrez la commande suivante à l'invite de commandes :

```console
gacutil /i publisherPolicyAssemblyFile
```

La commande `policy.1.0.myAssembly.dll` suivante s’ajoute à la cache d’assemblage global.

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> L’assemblée des politiques de l’éditeur ne peut être ajoutée `/link` au cache d’assemblage global à moins que le dossier de politique originale de l’éditeur spécifié dans l’argumentation ne soit situé dans le même répertoire que l’assemblée.

## <a name="see-also"></a>Voir aussi

- [Programmation à l’aide d’assemblys](../../standard/assembly/index.md)
- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Configuration des applications à l'aide de fichiers de configuration](index.md)
- [Paramètres de durée d’exécution Schema](./file-schema/runtime/index.md)
- [Configuration Fichier Schema](./file-schema/index.md)
- [Redirection des versions d'assemblys](redirect-assembly-versions.md)
