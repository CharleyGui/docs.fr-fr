---
title: Débogage des requêtes LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: a82fd3e99a556daf40e5c65a16cf20278f38ea26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785211"
---
# <a name="debugging-linq-to-dataset-queries"></a>Débogage des requêtes LINQ to DataSet

Visual Studio prend en charge le débogage de code LINQ to DataSet. Toutefois, il existe des différences entre le débogage LINQ to DataSet code et le code managé non LINQ to DataSet. La plupart des fonctionnalités de débogage fonctionnent avec les instructions LINQ to DataSet, y compris l’exécution pas à pas, la définition de points d’arrêt et l’affichage des résultats affichés dans les fenêtres du débogueur. Toutefois, l’exécution différée des requêtes dans a certains effets secondaires que vous devez prendre en compte lors du débogage LINQ to DataSet code et il existe certaines limitations à l’utilisation de modifier & continuer. Cette rubrique traite des aspects du débogage qui sont propres à LINQ to DataSet par rapport au code managé non LINQ to DataSet.  
  
## <a name="viewing-results"></a>Affichage des résultats  
 Vous pouvez afficher le résultat d’une instruction LINQ to DataSet à l’aide des DataTips, de la Fenêtre Espion et de la boîte de dialogue Espion express. En utilisant une fenêtre source, vous pouvez suspendre le pointeur sur une requête dans la fenêtre source pour afficher un DataTip. Vous pouvez copier une variable LINQ to DataSet et la coller dans la Fenêtre Espion ou la boîte de dialogue Espion express. Dans LINQ to DataSet, une requête n’est pas évaluée lorsqu’elle est créée ou déclarée, mais uniquement lors de l’exécution de la requête. C’est ce que l’on appelle *l’exécution différée*. Par conséquent, la variable de requête ne possède de valeur que lorsqu'elle est évaluée. Pour plus d’informations, consultez [requêtes dans LINQ to DataSet](queries-in-linq-to-dataset.md).  
  
 Pour afficher les résultats d'une requête, le débogueur doit l'évaluer. Cette évaluation implicite se produit lorsque vous affichez un LINQ to DataSet résultat de la requête dans le débogueur et que vous devez prendre en compte certains effets. Chaque évaluation de la requête prend du temps. Le développement du nœud de résultats est long. Ainsi, pour certaines requêtes, une évaluation répétée peut diminuer considérablement les performances. L'évaluation d'une requête provoque aussi des effets secondaires, à savoir des modifications de la valeur des données ou de l'état du programme. Toutefois, les requêtes ne présentent pas toutes des effets secondaires. Pour savoir si une requête peut être évaluée sans risque et sans effets secondaires, vous devez comprendre le code qui implémente la requête. Pour plus d’informations, consultez [effets secondaires et expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Modifier & Continuer  
 Modifier & Continuer ne prend pas en charge les modifications apportées aux requêtes LINQ to DataSet. Si vous ajoutez, supprimez ou modifiez une instruction LINQ to DataSet au cours d’une session de débogage, une boîte de dialogue s’affiche pour vous indiquer que la modification n’est pas prise en charge par modifier & continuer. À ce stade, vous pouvez annuler les modifications apportées ou arrêter la session de débogage et redémarrer une nouvelle session avec le code modifié.  
  
 En outre, modifier & Continuer ne prend pas en charge la modification du type ou de la valeur d’une variable utilisée dans une instruction LINQ to DataSet. Ici aussi, vous pouvez annuler les modifications apportées ou arrêter et redémarrer la session de débogage.  
  
 C# Dans Visual Studio, vous ne pouvez pas utiliser modifier & continuer dans un code d’une méthode qui contient une requête LINQ to DataSet.  
  
 Dans Visual Basic dans Visual Studio, vous pouvez utiliser modifier & Continuer sur du code non LINQ to DataSet, même dans une méthode qui contient une requête LINQ to DataSet. Vous pouvez ajouter ou supprimer du code avant l’instruction LINQ to DataSet, même si les modifications affectent le numéro de ligne de la requête LINQ to DataSet. Votre expérience de débogage Visual Basic pour le code non LINQ to DataSet reste identique à celle qu’elle avait avant l’introduction de LINQ to DataSet. Toutefois, vous ne pouvez pas modifier, ajouter ou supprimer une requête LINQ to DataSet, sauf si vous arrêtez le débogage pour appliquer les modifications.  
  
## <a name="see-also"></a>Voir aussi

- [Débogage du code managé](/visualstudio/debugger/debugging-managed-code)
- [Guide de programmation](programming-guide-linq-to-dataset.md)
