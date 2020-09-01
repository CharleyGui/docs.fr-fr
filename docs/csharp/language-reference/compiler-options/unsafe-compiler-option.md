---
description: -unsafe (Options du compilateur C#)
title: -unsafe (Options du compilateur C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140839"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (Options du compilateur C#)

L’option de compilateur **-unsafe** permet la compilation de code utilisant le mot clé [unsafe](../keywords/unsafe.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Notes

Pour plus d’informations sur le code unsafe, consultez [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez la page **Propriétés** du projet.  
  
2. Cliquez sur la page de propriétés **Générer**.  
  
3. Cochez la case **Autoriser le code unsafe**.  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Pour ajouter cette option dans un fichier csproj

Ouvrez le fichier .csproj d’un projet et ajoutez les éléments suivants :

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.  
  
## <a name="example"></a>Exemple

Compilez `in.cs` selon le mode non sécurisé :  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
