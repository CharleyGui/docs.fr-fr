---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: a818fd46bd93682f0bede1d22b8cbc2ca6467a40
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716738"
---
# <a name="-doc"></a>-doc
Traite les commentaires de documentation pour les diriger vers un fichier XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-doc[+ | -]  
```

ou  

```console
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`+` &#124; `-`|Facultatif. Si vous spécifiez +, ou simplement `-doc`, le compilateur génère des informations de documentation et les place dans un fichier XML. Si vous spécifiez `-`, ce qui équivaut à ne pas spécifier `-doc`, aucune information de documentation n’est créée.|  
|`file`|Obligatoire si l'option `-doc:` est utilisée. Spécifie le fichier XML de sortie, qui est renseigné avec les commentaires des fichiers de code source de la compilation. Si le nom de fichier contient un espace, placez-le entre des guillemets (" ").|  
  
## <a name="remarks"></a>Notes  
 L’option `-doc` contrôle si le compilateur génère un fichier XML contenant les commentaires de documentation. Si vous utilisez la syntaxe `-doc:file`, le paramètre `file` spécifie le nom du fichier XML. Si vous utilisez `-doc` ou `-doc+`, le compilateur prend le nom de fichier XML du fichier exécutable ou de la bibliothèque en cours de création. Si vous utilisez `-doc-` ou que vous ne spécifiez pas l’option `-doc`, le compilateur ne crée pas de fichier XML.  
  
 Dans les fichiers de code source, des commentaires de documentation peuvent précéder les définitions suivantes :  
  
- Types définis par l’utilisateur ([classe](../../../visual-basic/language-reference/statements/class-statement.md), [interface](../../../visual-basic/language-reference/statements/interface-statement.md), etc.)  
  
- Membres (champ, [événement](../../../visual-basic/language-reference/statements/event-statement.md), [propriété](../../../visual-basic/language-reference/statements/property-statement.md), [fonction](../../../visual-basic/language-reference/statements/function-statement.md), [sous-routine](../../../visual-basic/language-reference/statements/sub-statement.md), etc.)  
  
 Pour utiliser le fichier XML généré avec la fonctionnalité [IntelliSense](/visualstudio/ide/using-intellisense) de Visual Studio, faites en sorte que le nom du fichier XML soit identique à l’assembly que vous souhaitez prendre en charge. Vérifiez que le fichier XML se trouve dans le même répertoire que l’assembly. De cette façon, quand l’assembly est référencé dans le projet Visual Studio, le fichier .xml est aussi localisé. Les fichiers de documentation XML ne sont pas nécessaires au bon fonctionnement d’IntelliSense avec du code dans un projet ou dans des projets référencés par un projet.  
  
 Le fichier XML contient les balises `<assembly></assembly>`, sauf si vous effectuez la compilation avec `-target:module`. Ces balises spécifient le nom du fichier contenant le manifeste d’assembly pour le fichier de sortie de la compilation.  
  
 Pour découvrir comment générer de la documentation à partir de commentaires dans votre code, consultez [Balises de commentaires XML](../../../visual-basic/language-reference/xmldoc/index.md).  
  
|Pour définir -doc dans l’environnement de développement intégré Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **compiler** .<br />3. Définissez la valeur dans la zone **générer le fichier de documentation XML** .|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple, consultez [Documentation de votre code avec le langage XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Documentation de votre code avec le langage XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
