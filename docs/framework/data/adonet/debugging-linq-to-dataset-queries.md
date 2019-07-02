---
title: Débogage des requêtes LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 38eda9f352c4a8d8590e5e57b48c694eadd0397b
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67503983"
---
# <a name="debugging-linq-to-dataset-queries"></a>Débogage des requêtes LINQ to DataSet

Visual Studio prend en charge le débogage de LINQ au code du jeu de données. Toutefois, il existe certaines différences entre le débogage de LINQ à code de jeu de données et non-LINQ to DataSet managé code. Fonctionnalités de débogage plus fonctionnent avec LINQ aux instructions de jeu de données, y compris l’exécution pas à pas, la définition des points d’arrêt et la consultation des résultats dans les fenêtres du débogueur. Toutefois, l’exécution de requête différée dans a des effets dont vous devez tenir compte lors du débogage LINQ au code du jeu de données et il existe certaines limitations à l’utilisation de modifier & Continuer. Cette rubrique traite des aspects du débogage qui sont uniques à LINQ to DataSet par rapport aux non-LINQ to DataSet managé code.  
  
## <a name="viewing-results"></a>Affichage des résultats  
 Vous pouvez afficher le résultat de LINQ to DataSet instruction à l’aide des DataTips, de la fenêtre Espion et de la boîte de dialogue Espion express. En utilisant une fenêtre source, vous pouvez suspendre le pointeur sur une requête dans la fenêtre source pour afficher un DataTip. Vous pouvez copier un LINQ à DataSet variable et collez-le dans la fenêtre Espion ou la boîte de dialogue Espion express. Dans LINQ to DataSet, une requête n’est pas évaluée lorsqu’elle est créée ou déclarée, mais uniquement lorsque la requête est exécutée. Il s’agit *exécution différée*. Par conséquent, la variable de requête ne possède de valeur que lorsqu'elle est évaluée. Pour plus d’informations, consultez [requêtes dans LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Pour afficher les résultats d'une requête, le débogueur doit l'évaluer. Cette évaluation implicite se produit lorsque vous affichez un LINQ au résultat de requête de DataSet dans le débogueur, et elle entraîne quelques effets dont vous devez envisager. Chaque évaluation de la requête prend du temps. Le développement du nœud de résultats est long. Ainsi, pour certaines requêtes, une évaluation répétée peut diminuer considérablement les performances. L'évaluation d'une requête provoque aussi des effets secondaires, à savoir des modifications de la valeur des données ou de l'état du programme. Toutefois, les requêtes ne présentent pas toutes des effets secondaires. Pour savoir si une requête peut être évaluée sans risque et sans effets secondaires, vous devez comprendre le code qui implémente la requête. Pour plus d’informations, consultez [effets secondaires et Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Modifier & Continuer  
 Modifier & Continuer ne prend pas en charge les modifications apportées à LINQ aux requêtes de DataSet. Si vous ajoutez, supprimez ou modifiez un LINQ à l’instruction de jeu de données pendant une session de débogage, une boîte de dialogue s’affiche pour vous signaler à que la modification n’est pas pris en charge par Modifier & Continuer. À ce stade, vous pouvez annuler les modifications apportées ou arrêter la session de débogage et redémarrer une nouvelle session avec le code modifié.  
  
 De plus, Modifier & Continuer ne prend pas en charge la modification du type ou la valeur d’une variable qui est utilisée dans LINQ to DataSet instruction. Ici aussi, vous pouvez annuler les modifications apportées ou arrêter et redémarrer la session de débogage.  
  
 Dans Visual C# dans Visual Studio, vous ne pouvez pas utiliser Modifier & Continuer dans un code d’une méthode qui contient une requête LINQ to DataSet.  
  
 Dans Visual Basic dans Visual Studio, vous pouvez utiliser Modifier & Continuer sur non-code LINQ to DataSet, même dans une méthode qui contient une requête LINQ to DataSet. Vous pouvez ajouter ou supprimer du code avant le LINQ to DataSet instruction, même si les modifications affectent le numéro de ligne de la requête LINQ to DataSet. Votre expérience pour les non-LINQ to DataSet code de débogage de Visual Basic reste la même telle qu’elle était avant l’introduction de LINQ to DataSet. Vous ne pouvez pas modifier, ajouter ou supprimer une requête LINQ to DataSet, toutefois, sauf si vous arrêtez le débogage pour appliquer les modifications.  
  
## <a name="see-also"></a>Voir aussi

- [Débogage du code managé](/visualstudio/debugger/debugging-managed-code)
- [Guide de programmation](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
