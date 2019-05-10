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
ms.openlocfilehash: a2bd6ca11072113d8acff78032c19d48c30933c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615125"
---
# <a name="synclock-statement"></a>SyncLock, instruction
Acquiert un verrou exclusif pour un bloc d’instructions avant d’exécuter le bloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Composants  
 `lockobject`  
 Obligatoire. Expression qui correspond à une référence d’objet.  
  
 `block`  
 Facultatif. Bloc d’instructions à exécuter lorsque le verrou est acquis.  
  
 `End SyncLock`  
 Met fin à une `SyncLock` bloc.  
  
## <a name="remarks"></a>Notes  
 La `SyncLock` instruction permet de garantir que plusieurs threads n’exécutent pas le bloc d’instructions en même temps. `SyncLock` empêche chaque thread d’entrer dans le bloc jusqu'à ce qu’aucun autre thread ne l’exécute.  
  
 L’utilisation la plus courante de `SyncLock` consiste à protéger les données à partir de la mise à jour par plusieurs threads simultanément. Si les instructions qui manipulent les données doivent être exécutées sans interruption, placez-les à l’intérieur d’un `SyncLock` bloc.  
  
 Un bloc d’instructions protégé par un verrou exclusif est parfois appelé un *section critique*.  
  
## <a name="rules"></a>Règles  
  
- Création de branche. Vous ne pouvez pas créer de branche dans un `SyncLock` empêche en dehors du bloc.  
  
- Valeur de l’objet verrou. La valeur de `lockobject` ne peut pas être `Nothing`. Vous devez créer l’objet verrou avant de l’utiliser dans un `SyncLock` instruction.  
  
     Vous ne pouvez pas modifier la valeur de `lockobject` pendant l’exécution d’un `SyncLock` bloc. Le mécanisme exige que l’objet de verrouillage reste inchangé.  
  
- Vous ne pouvez pas utiliser le [Await](../../../visual-basic/language-reference/operators/await-operator.md) opérateur dans un `SyncLock` bloc.  
  
## <a name="behavior"></a>Comportement  
  
- Mécanisme. Lorsqu’un thread atteint le `SyncLock` instruction, elle prend la valeur la `lockobject` expression et suspend l’exécution jusqu'à ce qu’il acquiert un verrou exclusif sur l’objet retourné par l’expression. Lorsqu’un autre thread atteint le `SyncLock` instruction, elle ne pas acquérir un verrou jusqu'à ce que le premier thread exécute le `End SyncLock` instruction.  
  
- Les données protégées. Si `lockobject` est un `Shared` variable, le verrou exclusif empêche un thread dans n’importe quelle instance de la classe d’exécuter le `SyncLock` bloquer pendant que n’importe quel autre thread l’exécute. Cela protège les données qui sont partagées entre toutes les instances.  
  
     Si `lockobject` est une variable d’instance (pas `Shared`), le verrou empêche un thread en cours d’exécution dans l’instance actuelle à partir de l’exécution de la `SyncLock` bloc en même temps qu’un autre thread dans la même instance. Cela protège les données conservées par l’instance.  
  
- Acquisition et la libération. A `SyncLock` bloc se comporte comme un `Try...Finally` dans laquelle le `Try` bloc acquiert un verrou exclusif sur `lockobject` et `Finally` bloc le libère. Pour cette raison, le `SyncLock` bloc garantit la libération du verrou, quelle que soit la manière dont vous quittez le bloc. Cela est vrai même en cas d’une exception non gérée.  
  
- Appels de Framework. Le `SyncLock` bloc acquiert et libère le verrou exclusif en appelant le `Enter` et `Exit` méthodes de la `Monitor` classe dans le <xref:System.Threading> espace de noms.  
  
## <a name="programming-practices"></a>Pratiques de programmation  
 Le `lockobject` expression doit toujours correspondre à un objet qui appartienne exclusivement à votre classe. Vous devez déclarer un `Private` variable d’objet pour protéger les données appartenant à l’instance actuelle, ou un `Private Shared` variable d’objet pour protéger les données communes à toutes les instances.  
  
 Vous ne devez pas utiliser le `Me` données mot clé pour fournir un verrou d’objet par exemple. Si le code externe à votre classe comporte une référence à une instance de votre classe, il pourrait utiliser cette référence comme un objet de verrouillage pour un `SyncLock` bloc complètement différent du vôtre, protégeant des données différentes. De cette façon, votre classe et l’autre classe peuvent bloquer mutuellement à partir de l’exécution de leurs indépendants `SyncLock` blocs. Le verrouillage de la même façon sur une chaîne peut être problématique dans la mesure où tout autre code dans le processus à l’aide de la même chaîne partagera le même verrou.  
  
 Vous devez également utiliser pas le `Me.GetType` méthode pour fournir un objet de verrouillage pour les données partagées. Il s’agit, car `GetType` retourne toujours le même `Type` objet pour un nom de classe donné. Code externe pourrait appeler `GetType` sur votre classe et obtenir le même objet de verrouillage que vous utilisez. Cela se traduirait dans ces deux classes blocage eux à partir de leurs `SyncLock` blocs.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple suivant montre une classe qui gère une liste simple de messages. Il stocke les messages dans un tableau et le dernier élément utilisé de ce tableau dans une variable. Le `addAnotherMessage` procédure incrémente le dernier élément et stocke le nouveau message. Ces deux opérations sont protégées par le `SyncLock` et `End SyncLock` instructions, car une fois que le dernier élément a été incrémenté, le nouveau message doit être stocké avant que tout autre thread peut incrémenter le dernier élément à nouveau.  
  
 Si le `simpleMessageList` classe partagée d’une liste de messages entre toutes ses instances, les variables `messagesList` et `messagesLast` sont déclarées comme `Shared`. Dans ce cas, la variable `messagesLock` doit également être `Shared`, afin qu’il n’y aurait un objet verrou unique utilisé par chaque instance.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Description  
 L’exemple suivant utilise des threads et `SyncLock`. Tant que le `SyncLock` instruction est présente, le bloc d’instructions est une section critique et `balance` ne devient jamais un nombre négatif. Vous pouvez commenter le `SyncLock` et `End SyncLock` instructions pour voir l’effet de la mise la `SyncLock` mot clé.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>Commentaires  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Vue d’ensemble des primitives de synchronisation](../../../standard/threading/overview-of-synchronization-primitives.md)
