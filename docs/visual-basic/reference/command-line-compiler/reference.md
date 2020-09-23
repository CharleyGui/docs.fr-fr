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
ms.openlocfilehash: b489a164e56a5e3bdbf7e3cdf24ec330fadedf38
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097551"
---
# <a name="-reference-visual-basic"></a>-Reference (Visual Basic)

Fait en sorte que le compilateur rende les informations de type dans les assemblys spécifiés disponibles pour le projet en cours de compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-reference:fileList  
```

or

```console
-r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`fileList`|Obligatoire. Liste délimitée par des virgules des noms de fichiers d’assembly. Si le nom de fichier contient un espace, placez-le entre des guillemets.|  
  
## <a name="remarks"></a>Notes  

 Le ou les fichiers que vous importez doivent contenir des métadonnées d’assembly. Seuls les types publics sont visibles à l’extérieur de l’assembly. L’option [-addmodule](addmodule.md) importe les métadonnées d’un module.  
  
 Si vous référencez un assembly (assembly A) qui référence lui-même un autre assembly (assembly B), vous devez référencer l’assembly B si :  
  
- Un type de l’Assembly A hérite d’un type ou implémente une interface de l’Assembly B.  
  
- Un champ, une propriété, un événement ou une méthode qui a un type de retour ou un type de paramètre de l’Assembly B est appelé.  
  
 Utilisez [-LIBPATH](libpath.md) pour spécifier le répertoire dans lequel se trouvent une ou plusieurs références d’assembly.  
  
 Pour que le compilateur reconnaisse un type dans un assembly (et non un module), il doit être forcé de résoudre le type. Vous pouvez, par exemple, définir une instance du type. D’autres méthodes sont disponibles pour résoudre les noms de types dans un assembly pour le compilateur. Par exemple, si vous héritez d’un type dans un assembly, le nom de type devient alors connu du compilateur.  
  
 Le fichier réponse Vbc. rsp, qui référence les assemblys couramment utilisés .NET Framework, est utilisé par défaut. Utilisez `-noconfig` si vous ne souhaitez pas que le compilateur utilise vbc. rsp.  
  
 La forme abrégée de `-reference` est `-r`.  
  
## <a name="example"></a>Exemple  

 La commande suivante compile le fichier source `Input.vb` et les assemblys de référence à partir de `Metad1.dll` et `Metad2.dll` pour produire `Out.exe` .  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-noconfig](noconfig.md)
- [-cible (Visual Basic)](target.md)
- [Public](../../language-reference/modifiers/public.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
