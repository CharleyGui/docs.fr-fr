---
title: SyncLock, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: e981ee727b66ecda392014fd3ee8ca6f1526cd2e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578898"
---
# <a name="synclock-statement"></a>SyncLock, instruction
Acquiert un verrou exclusif pour un bloc d’instructions avant d’exécuter le bloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Composants  
 `lockobject`  
 Requis. Expression qui prend la valeur d’une référence d’objet.  
  
 `block`  
 Optionnel. Bloc d’instructions à exécuter lorsque le verrou est acquis.  
  
 `End SyncLock`  
 Met fin à un bloc de `SyncLock`.  
  
## <a name="remarks"></a>Notes  
 L’instruction `SyncLock` garantit que plusieurs threads n’exécutent pas le bloc d’instructions en même temps. `SyncLock` empêche chaque thread d’entrer dans le bloc jusqu’à ce qu’aucun autre thread l’exécute.  
  
 L’utilisation la plus courante de `SyncLock` consiste à empêcher la mise à jour des données par plusieurs threads simultanément. Si les instructions qui manipulent les données doivent se terminer sans interruption, placez-les à l’intérieur d’un bloc de `SyncLock`.  
  
 Un bloc d’instructions protégé par un verrou exclusif est parfois appelé une *section critique*.  
  
## <a name="rules"></a>Règles  
  
- Branche. Vous ne pouvez pas créer de branche dans un bloc `SyncLock` à partir de l’extérieur du bloc.  
  
- Valeur de l’objet Lock. La valeur de `lockobject` ne peut pas être `Nothing`. Vous devez créer l’objet Lock avant de l’utiliser dans une instruction `SyncLock`.  
  
     Vous ne pouvez pas modifier la valeur de `lockobject` lors de l’exécution d’un bloc `SyncLock`. Le mécanisme requiert que l’objet Lock reste inchangé.  
  
- Vous ne pouvez pas utiliser l’opérateur [await](../../../visual-basic/language-reference/operators/await-operator.md) dans un bloc `SyncLock`.  
  
## <a name="behavior"></a>Comportement  
  
- Procédé. Lorsqu’un thread atteint l’instruction `SyncLock`, il évalue l’expression `lockobject` et interrompt l’exécution jusqu’à ce qu’il acquière un verrou exclusif sur l’objet retourné par l’expression. Lorsqu’un autre thread atteint l’instruction `SyncLock`, il n’obtient pas de verrou tant que le premier thread n’a pas exécuté l’instruction `End SyncLock`.  
  
- Données protégées. Si `lockobject` est une variable `Shared`, le verrou exclusif empêche un thread dans une instance de la classe d’exécuter le bloc `SyncLock` alors que tout autre thread l’exécute. Cela protège les données partagées entre toutes les instances.  
  
     Si `lockobject` est une variable d’instance (et non `Shared`), le verrou empêche un thread s’exécutant dans l’instance actuelle d’exécuter le bloc `SyncLock` en même temps qu’un autre thread dans la même instance. Cela protège les données gérées par l’instance individuelle.  
  
- Acquisition et mise en version. Un bloc `SyncLock` se comporte comme une construction `Try...Finally` dans laquelle le bloc `Try` acquiert un verrou exclusif sur `lockobject` et le bloc `Finally` le libère. Pour cette raison, le bloc de `SyncLock` garantit la libération du verrou, quelle que soit la façon dont vous quittez le bloc. Cela est vrai même dans le cas d’une exception non gérée.  
  
- Appels au Framework. Le bloc `SyncLock` acquiert et libère le verrou exclusif en appelant les méthodes `Enter` et `Exit` de la classe `Monitor` dans l’espace de noms <xref:System.Threading>.  
  
## <a name="programming-practices"></a>Pratiques de programmation  
 L’expression `lockobject` doit toujours correspondre à un objet qui appartient exclusivement à votre classe. Vous devez déclarer une variable objet `Private` pour protéger les données appartenant à l’instance actuelle, ou une variable objet `Private Shared` pour protéger les données communes à toutes les instances.  
  
 Vous ne devez pas utiliser le mot clé `Me` pour fournir un objet Lock pour les données d’instance. Si le code externe à votre classe contient une référence à une instance de votre classe, il peut utiliser cette référence comme objet de verrouillage pour un bloc `SyncLock` complètement différent de la vôtre, protégeant des données différentes. De cette façon, votre classe et l’autre classe peuvent se bloquer l’exécution de leurs blocs `SyncLock` non liés. De même, le verrouillage sur une chaîne peut être problématique, car tout autre code dans le processus qui utilise la même chaîne partagera le même verrou.  
  
 Vous ne devez pas non plus utiliser la méthode `Me.GetType` pour fournir un objet Lock pour les données partagées. Cela est dû au fait que `GetType` retourne toujours le même objet `Type` pour un nom de classe donné. Le code externe peut appeler `GetType` sur votre classe et obtenir le même objet de verrouillage que vous utilisez. Cela entraînerait le blocage des deux classes de leurs blocs `SyncLock`.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple suivant illustre une classe qui gère une simple liste de messages. Elle contient les messages d’un tableau et le dernier élément utilisé de ce tableau dans une variable. La procédure `addAnotherMessage` incrémente le dernier élément et stocke le nouveau message. Ces deux opérations sont protégées par les instructions `SyncLock` et `End SyncLock`, car une fois que le dernier élément a été incrémenté, le nouveau message doit être stocké avant que tout autre thread puisse incrémenter à nouveau le dernier élément.  
  
 Si la classe `simpleMessageList` a partagé une liste de messages parmi toutes ses instances, les variables `messagesList` et `messagesLast` sont déclarées comme `Shared`. Dans ce cas, la variable `messagesLock` doit également être `Shared`, afin qu’il y ait un seul objet de verrouillage utilisé par chaque instance.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Description  
 L’exemple suivant utilise des threads et des `SyncLock`. Tant que l’instruction `SyncLock` est présente, le bloc d’instructions est une section critique et `balance` ne devient jamais un nombre négatif. Vous pouvez commenter les instructions `SyncLock` et `End SyncLock` pour voir l’effet de la sortie du mot clé `SyncLock`.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Comments  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Vue d’ensemble des primitives de synchronisation](../../../standard/threading/overview-of-synchronization-primitives.md)
