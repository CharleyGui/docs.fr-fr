---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 35e02d1ad4409e754c2466f7d0ae7e68214772e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716704"
---
# <a name="-reference-visual-basic"></a>-Reference (Visual Basic)
Fait en sorte que le compilateur rende les informations de type dans les assemblys spécifiés disponibles pour le projet en cours de compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-reference:fileList  
```

ou

```console
-r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`fileList`|Obligatoire. Liste délimitée par des virgules des noms de fichiers d’assembly. Si le nom de fichier contient un espace, placez-le entre des guillemets.|  
  
## <a name="remarks"></a>Notes  
 Le ou les fichiers que vous importez doivent contenir des métadonnées d’assembly. Seuls les types publics sont visibles à l’extérieur de l’assembly. L’option [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) importe les métadonnées d’un module.  
  
 Si vous référencez un assembly (assembly A) qui référence lui-même un autre assembly (assembly B), vous devez référencer l’assembly B si :  
  
- Un type de l’Assembly A hérite d’un type ou implémente une interface de l’Assembly B.  
  
- Un champ, une propriété, un événement ou une méthode qui a un type de retour ou un type de paramètre de l’Assembly B est appelé.  
  
 Utilisez [-LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) pour spécifier le répertoire dans lequel se trouvent une ou plusieurs références d’assembly.  
  
 Pour que le compilateur reconnaisse un type dans un assembly (et non un module), il doit être forcé de résoudre le type. Vous pouvez, par exemple, définir une instance du type. D’autres méthodes sont disponibles pour résoudre les noms de types dans un assembly pour le compilateur. Par exemple, si vous héritez d’un type dans un assembly, le nom de type devient alors connu du compilateur.  
  
 Le fichier réponse Vbc. rsp, qui référence les assemblys couramment utilisés .NET Framework, est utilisé par défaut. Utilisez `-noconfig` si vous ne souhaitez pas que le compilateur utilise vbc. rsp.  
  
 La forme abrégée de `-reference` est `-r`.  
  
## <a name="example"></a>Exemple  
 La commande suivante compile `Input.vb` le fichier source et les assemblys de référence `Metad1.dll` à `Metad2.dll` partir de `Out.exe`et pour produire.  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-cible (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
