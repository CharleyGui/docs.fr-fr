---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 69781dff1474e42ae5f735fdefd694c6447636b5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085254"
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

 L' `-imports` option importe tout espace de noms défini dans l’ensemble actuel de fichiers sources ou à partir d’un assembly référencé.  
  
 Les membres d’un espace de noms spécifié avec `-imports` sont disponibles pour tous les fichiers de code source de la compilation. Utilisez l' [instruction Imports (espace de noms et type .net)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) pour utiliser un espace de noms dans un fichier de code source unique.  
  
|Pour définir-Imports dans l’environnement de développement intégré Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **références** .<br />3. Entrez le nom de l’espace de noms dans la zone en regard du bouton **Ajouter une importation utilisateur** .<br />4. cliquez sur le bouton **Ajouter une importation d’utilisateur** .|  
  
## <a name="example"></a>Exemple  

 Le code suivant compile lorsque `-imports:system.globalization` est spécifié. Sans cela, la réussite de la compilation requiert qu’une `Imports System.Globalization` instruction soit incluse au début du fichier de code source, ou que la propriété soit qualifiée complète en tant que `System.Globalization.CultureInfo.CurrentCulture.Name` .

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Références et instruction Imports](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
