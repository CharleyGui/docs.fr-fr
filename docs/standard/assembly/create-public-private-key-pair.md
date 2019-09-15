---
title: 'Procédure : Créer une paire de clés publique/privée'
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 62c38494e29541bd490d69ccc8de485217b9514a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991702"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Procédure : Créer une paire de clés publique/privée

Pour signer un assembly avec un nom fort, vous devez disposer d’une paire de clés publique/privée. Cette paire de clés de chiffrement public et privé est utilisée lors de la compilation pour créer un assembly avec nom fort. Vous pouvez créer une paire de clés à l’aide de l’[outil Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md). Les fichiers de paire de clés ont généralement une extension *. snk* .

> [!NOTE]
> Dans Visual Studio, les C# pages de propriétés du projet et Visual Basic comprennent un onglet **signature** qui vous permet de sélectionner des fichiers de clé existants ou de générer de nouveaux fichiers de clé sans utiliser *sn. exe*. Dans Visual C++, vous pouvez spécifier l’emplacement d’un fichier de clés existant dans la page de propriétés **Avancé** de la section **Éditeur de liens**, dans la section **Propriétés de Configuration** de la fenêtre **Pages de propriétés**. L’utilisation de l' <xref:System.Reflection.AssemblyKeyFileAttribute> attribut pour identifier les paires de fichiers de clés est devenue obsolète à partir de Visual Studio 2005.

## <a name="create-a-key-pair"></a>Créer une paire de clés

Pour créer une paire de clés, à l’invite de commandes, tapez la commande suivante :

**sn –k** \<*nom de fichier*>

Dans cette commande, *nom de fichier* est le nom du fichier de sortie contenant la paire de clés.

L’exemple suivant crée une paire de clés appelée *sgKey. snk*.

```cmd
sn -k sgKey.snk
```

Si vous avez l’intention de temporiser la signature d’un assembly et que vous contrôlez la paire de clés entière (ce qui est improbable en dehors des scénarios de test), vous pouvez utiliser les commandes suivantes pour générer une paire de clés et ensuite en extraire la clé publique dans un fichier distinct. Commencez par créer la paire de clés :

```cmd
sn -k keypair.snk
```

Procédez ensuite à l’extraction de la clé publique de la paire de clés et copiez-la dans un fichier distinct :

```cmd
sn -p keypair.snk public.snk
```

Une fois que vous avez créé la paire de clés, vous devez placer le fichier à l’endroit où les outils de signature de nom fort peuvent le trouver.

Lorsque vous signez un assembly avec un nom fort, l’utilitaire [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) recherche le fichier de clés par rapport au répertoire en cours et au répertoire de sortie. Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez vous contenter de copier la clé dans le répertoire en cours contenant vos modules de code.

Si vous utilisez une version antérieure de Visual Studio qui ne dispose pas d’onglet **Signature** dans les propriétés du projet, l’emplacement du fichier de clés recommandé est le répertoire du projet avec l’attribut de fichier spécifié comme suit :

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a>Voir aussi

- [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)
