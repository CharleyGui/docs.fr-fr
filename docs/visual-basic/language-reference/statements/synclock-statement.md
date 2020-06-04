---
title: SyncLock, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: fd932a20af274faf2b56136a94675b28399989b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404159"
---
# <a name="synclock-statement"></a>SyncLock, instruction
Acquiert un verrou exclusif pour un bloc d’instructions avant d’exécuter le bloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Éléments  
 `lockobject`  
 Obligatoire. Expression qui prend la valeur d’une référence d’objet.  
  
 `block`  
 Facultatif. Bloc d’instructions à exécuter lorsque le verrou est acquis.  
  
 `End SyncLock`  
 Met fin à un `SyncLock` bloc.  
  
## <a name="remarks"></a>Notes  
 L' `SyncLock` instruction garantit que plusieurs threads n’exécutent pas le bloc d’instructions en même temps. `SyncLock`empêche chaque thread d’entrer dans le bloc jusqu’à ce qu’aucun autre thread l’exécute.  
  
 L’utilisation la plus courante de `SyncLock` est de protéger les données contre la mise à jour simultanée de plusieurs threads. Si les instructions qui manipulent les données doivent se terminer sans interruption, placez-les à l’intérieur d’un `SyncLock` bloc.  
  
 Un bloc d’instructions protégé par un verrou exclusif est parfois appelé une *section critique*.  
  
## <a name="rules"></a>Règles  
  
- Branche. Vous ne pouvez pas créer de branche dans un `SyncLock` bloc en dehors du bloc.  
  
- Valeur de l’objet Lock. La valeur de `lockobject` ne peut pas être `Nothing` . Vous devez créer l’objet Lock avant de l’utiliser dans une `SyncLock` instruction.  
  
     Vous ne pouvez pas modifier la valeur de `lockobject` lors de l’exécution d’un `SyncLock` bloc. Le mécanisme requiert que l’objet Lock reste inchangé.  
  
- Vous ne pouvez pas utiliser l’opérateur [await](../operators/await-operator.md) dans un `SyncLock` bloc.  
  
## <a name="behavior"></a>Comportement  
  
- Procédé. Lorsqu’un thread atteint l' `SyncLock` instruction, il évalue l' `lockobject` expression et interrompt l’exécution jusqu’à ce qu’il acquière un verrou exclusif sur l’objet retourné par l’expression. Lorsqu’un autre thread atteint l' `SyncLock` instruction, il n’obtient pas de verrou tant que le premier thread n’a pas exécuté l' `End SyncLock` instruction.  
  
- Données protégées. Si `lockobject` est une `Shared` variable, le verrou exclusif empêche un thread dans une instance de la classe d’exécuter le `SyncLock` bloc alors que tout autre thread l’exécute. Cela protège les données partagées entre toutes les instances.  
  
     Si `lockobject` est une variable d’instance (not `Shared` ), le verrou empêche un thread s’exécutant dans l’instance actuelle d’exécuter le `SyncLock` bloc en même temps qu’un autre thread dans la même instance. Cela protège les données gérées par l’instance individuelle.  
  
- Acquisition et mise en version. Un `SyncLock` bloc se comporte comme une `Try...Finally` construction dans laquelle le `Try` bloc acquiert un verrou exclusif sur `lockobject` et le bloc le `Finally` libère. Pour cette raison, le `SyncLock` Bloc garantit la libération du verrou, quel que soit le mode de sortie du bloc. Cela est vrai même dans le cas d’une exception non gérée.  
  
- Appels au Framework. Le `SyncLock` bloc acquiert et libère le verrou exclusif en appelant les `Enter` `Exit` méthodes et de la `Monitor` classe dans l' <xref:System.Threading> espace de noms.  
  
## <a name="programming-practices"></a>Pratiques de programmation  
 L' `lockobject` expression doit toujours prendre la valeur d’un objet qui appartient exclusivement à votre classe. Vous devez déclarer une `Private` variable objet pour protéger les données appartenant à l’instance actuelle, ou une `Private Shared` variable objet pour protéger les données communes à toutes les instances.  
  
 Vous ne devez pas utiliser le `Me` mot clé pour fournir un objet Lock pour les données d’instance. Si le code externe à votre classe contient une référence à une instance de votre classe, il peut utiliser cette référence comme objet de verrouillage pour un `SyncLock` bloc complètement différent de la vôtre, protégeant les données différentes. De cette façon, votre classe et l’autre classe peuvent se bloquer l’exécution de leurs blocs non liés `SyncLock` . De même, le verrouillage sur une chaîne peut être problématique, car tout autre code dans le processus qui utilise la même chaîne partagera le même verrou.  
  
 Vous ne devez pas non plus utiliser la `Me.GetType` méthode pour fournir un objet Lock pour les données partagées. Cela est dû `GetType` au fait que retourne toujours le même `Type` objet pour un nom de classe donné. Le code externe peut appeler `GetType` votre classe et obtenir le même objet de verrouillage que vous utilisez. Cela entraînerait le blocage des deux classes de leurs `SyncLock` blocs.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple suivant illustre une classe qui gère une simple liste de messages. Elle contient les messages d’un tableau et le dernier élément utilisé de ce tableau dans une variable. La `addAnotherMessage` procédure incrémente le dernier élément et stocke le nouveau message. Ces deux opérations sont protégées par les `SyncLock` `End SyncLock` instructions et, car une fois que le dernier élément a été incrémenté, le nouveau message doit être stocké avant que tout autre thread puisse incrémenter à nouveau le dernier élément.  
  
 Si la `simpleMessageList` classe a partagé une liste de messages parmi toutes ses instances, les variables `messagesList` et `messagesLast` seraient déclarées comme `Shared` . Dans ce cas, la variable `messagesLock` doit également être `Shared` , afin qu’il y ait un seul objet de verrouillage utilisé par chaque instance.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Description  
 L’exemple suivant utilise des threads et `SyncLock` . Tant que l' `SyncLock` instruction est présente, le bloc d’instructions est une section critique et `balance` ne devient jamais un nombre négatif. Vous pouvez commenter les `SyncLock` `End SyncLock` instructions et pour voir l’effet de la sortie du `SyncLock` mot clé.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Commentaires  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Vue d’ensemble des primitives de synchronisation](../../../standard/threading/overview-of-synchronization-primitives.md)
