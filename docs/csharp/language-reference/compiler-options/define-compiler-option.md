---
title: -define (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 4a3622b6acc8ebe9c590b01b67074ae59396fc34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173742"
---
# <a name="-define-c-compiler-options"></a>-define (Options du compilateur C#)
L’option **-define** définit `name` comme symbole dans tous les fichiers de code source de votre programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Arguments  
 `name`, `name2`  
 Nom de chaque symbole que vous souhaitez définir.  
  
## <a name="remarks"></a>Notes   
 L’option **-define** revient à utiliser une directive de préprocesseur [#define](../preprocessor-directives/preprocessor-define.md), sauf que l’option de compilateur est appliquée à tous les fichiers du projet. Un symbole reste défini dans un fichier source jusqu’à ce qu’une directive [#undef](../preprocessor-directives/preprocessor-undef.md) dans le fichier source en supprime la définition. Quand vous utilisez l’option -define, une directive `#undef` dans un fichier n’a aucun effet sur les autres fichiers de code source du projet.  
  
 Vous pouvez utiliser les symboles créés par cette option avec [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md) et [#endif](../preprocessor-directives/preprocessor-endif.md) pour effectuer une compilation conditionnelle des fichiers sources.  
  
 **-d** est la forme abrégée de **-define**.  
  
 Pour définir plusieurs symboles avec **-define**, séparez chaque nom de symbole par un point-virgule ou une virgule. Par exemple :  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 Le compilateur C# lui-même ne définit aucun symbole ni aucune macro que vous pouvez utiliser dans votre code source ; toutes les définitions de symbole doivent être définies par l’utilisateur.  
  
> [!NOTE]
> La directive C# `#define` ne permet de donner une valeur à un symbole, comme dans les langages tels que C++. Par exemple, l’option `#define` ne peut pas être utilisée pour créer une macro ni définir une constante. Si vous devez définir une constante, utilisez une variable `enum`. Si vous souhaitez créer une macro de style C++, envisagez l’alternative que constituent les génériques. Comme les macros sont notoirement sujettes aux erreurs, C# n’autorise pas leur utilisation, mais fournit des solutions plus sûres.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez la page **Propriétés** du projet.  
  
2. Dans l’onglet **Générer**, tapez le symbole à définir dans la zone **Symboles de compilation conditionnelle**. Par exemple, si vous utilisez l’exemple de code qui suit, tapez simplement `xx` dans la zone de texte.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
## <a name="example"></a> Exemple  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test
{  
    public static void Main()
    {  
        #if (xx)
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
