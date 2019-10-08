---
title: -Imports (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 929e24a1ffd02d4e21ab1b925ddd59050b5d3cc4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005563"
---
# <a name="-imports-visual-basic"></a>-Imports (Visual Basic)
Importe des espaces de noms à partir d’un assembly spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`namespaceList`|Obligatoire. Liste délimitée par des virgules des espaces de noms à importer.|  
  
## <a name="remarks"></a>Notes  
 L’option `-imports` importe tout espace de noms défini dans l’ensemble actuel de fichiers sources ou à partir d’un assembly référencé.  
  
 Les membres d’un espace de noms spécifié avec `-imports` sont disponibles pour tous les fichiers de code source de la compilation. Utilisez l' [instruction Imports (espace de noms et type .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour utiliser un espace de noms dans un fichier de code source unique.  
  
|Pour définir/Imports dans l’environnement de développement intégré Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**. <br />2.  Cliquez sur l’onglet **Références**.<br />3.  Entrez le nom de l’espace de noms dans la zone en regard du bouton **Ajouter une importation utilisateur** .<br />4.  Cliquez sur le bouton **Ajouter une importation d’utilisateur** .|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile lorsque `/imports:system.globalization` est spécifié. Sans celui-ci, la réussite de la compilation nécessite soit qu’une instruction `Imports System.Globalization` soit incluse au début du fichier de code source, soit que la propriété soit entièrement qualifiée comme `System.Globalization.CultureInfo.CurrentCulture.Name`.

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
