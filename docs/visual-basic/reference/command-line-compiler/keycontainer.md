---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: be2ad1416e801398fb513593c7f3828e5488bfaf
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005525"
---
# <a name="-keycontainer"></a>-keycontainer
Spécifie un nom de conteneur de clé pour une paire de clés afin d'attribuer un nom fort à un assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`container`|Obligatoire. Fichier conteneur qui contient la clé. Placez le nom de fichier entre guillemets ("") si le nom contient un espace.|  
  
## <a name="remarks"></a>Notes  
 Le compilateur crée le composant partageable en insérant une clé publique dans le manifeste de l’assembly et en signant l’assembly final avec la clé privée. Pour générer un fichier de clé, tapez `sn -k file` à la ligne de commande. L' `-i` option installe la paire de clés dans un conteneur. Pour plus d’informations, consultez [sn. exe (outil Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Si vous compilez avec `-target:module`, le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly créé quand vous compilez un assembly avec [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Vous pouvez également spécifier cette option comme attribut personnalisé (<xref:System.Reflection.AssemblyKeyNameAttribute>) dans le code source de n'importe quel module MSIL (Microsoft Intermediate Language).  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Utilisez [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) si vous voulez obtenir un assembly partiellement signé.  
  
 Pour plus d’informations sur la signature d’un assembly [, consultez Création et utilisation d’assemblys avec nom fort](../../../standard/assembly/create-use-strong-named.md) .  
  
> [!NOTE]
> L' `-keycontainer` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile le fichier `Input.vb` source et spécifie un conteneur de clé.  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](../../../standard/assembly/index.md)
- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
