---
title: Composite personnalisé à l'aide de NativeActivity
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 57c724ad55c3aa2960e9a2d11fcd8419a94a0c72
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715173"
---
# <a name="custom-composite-using-native-activity"></a>Composite personnalisé à l'aide de NativeActivity
Cet exemple montre comment écrire un <xref:System.Activities.NativeActivity> qui planifie d'autres objets <xref:System.Activities.Activity> pour contrôler le flux d'exécution d'un workflow. Cet exemple utilise deux flux de contrôle communs, Sequence et While, pour illustrer cette procédure.

## <a name="sample-details"></a>Détails de l'exemple
 À partir de `MySequence`, la première chose à remarquer est qu'il dérive de <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> est l'objet <xref:System.Activities.Activity> qui expose la totalité de l'exécution du workflow via le <xref:System.Activities.NativeActivityContext> passé à la méthode `Execute`.

 `MySequence` expose une collection publique d'objets <xref:System.Activities.Activity> qui est remplie par l'auteur de workflow. Avant que le workflow ne soit exécuté, l'exécution du workflow appelle la méthode <xref:System.Activities.Activity.CacheMetadata%2A> sur chaque activité dans un workflow. Pendant ce processus, l'exécution établit des relations parent-enfant pour la portée des données et la gestion de la durée de vie. L’implémentation par défaut de la méthode <xref:System.Activities.Activity.CacheMetadata%2A> utilise la classe d’instance <xref:System.ComponentModel.TypeDescriptor> pour l’activité `MySequence` pour ajouter une propriété publique de type <xref:System.Activities.Activity> ou <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Activity>> comme enfants de l’activité `MySequence`.

 Chaque fois qu'une activité expose une collection publique d'activités enfants, il est probable que ces activités enfants partagent l'état. Il est recommandé à l'activité parent, dans ce cas `MySequence`, d'exposer également une collection de variables par le biais desquelles les activités enfants peuvent y parvenir. À l’instar des activités enfants, la méthode <xref:System.Activities.Activity.CacheMetadata%2A> ajoute des propriétés publiques de type <xref:System.Activities.Variable> ou <xref:System.Collections.IEnumerable>\<<xref:System.Activities.Variable>> comme variables associées à l’activité `MySequence`.

 Outre les variables publiques, manipulées par les enfants de `MySequence`, `MySequence` doit également effectuer le suivi de sa situation dans l'exécution de ses enfants. Il utilise une variable privée, `currentIndex`, pour ce faire. Cette variable est inscrite dans le cadre de l'environnement `MySequence` en ajoutant un appel à la méthode <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> dans la méthode `MySequence` de l'activité <xref:System.Activities.Activity.CacheMetadata%2A>. Les objets <xref:System.Activities.Activity> ajoutés à la collection `MySequence``Activities` ne peuvent pas accéder aux variables ajoutées de cette façon.

 Lorsque `MySequence` est exécuté par l'exécution, l'exécution appelle sa méthode <xref:System.Activities.NativeActivity.Execute%2A>, en lui passant un <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> est le proxy de l'activité dans l'exécution pour le déréférencement des arguments et des variables ainsi que la planification d'autres objets <xref:System.Activities.Activity>, ou `ActivityDelegates`. `MySequence` utilise une méthode `InternalExecute` pour encapsuler la logique de planification du premier enfant et tous les enfants suivants dans une méthode unique. Il commence par supprimer la référence du `currentIndex`. S'il est égal au nombre dans la collection `Activities`, la séquence est terminée, l'activité est retournée sans planifier de travail et l'exécution la déplace dans l'état <xref:System.Activities.ActivityInstanceState.Closed>. Si le `currentIndex` est inférieur au nombre d’activités, l’enfant suivant est obtenu à partir de la collection `Activities` et `MySequence` appelle <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, en passant l’enfant à planifier et une <xref:System.Activities.CompletionCallback> qui pointe vers la méthode `InternalExecute`. Enfin, le `currentIndex` est incrémenté et le contrôle est répercuté dans l'exécution. Tant qu'une instance de `MySequence` a un objet <xref:System.Activities.Activity> enfant planifié, l'exécution le considère comme étant dans l'état Exécution.

 Lorsque l'activité enfant est terminée, le <xref:System.Activities.CompletionCallback> est exécuté. La boucle continue à partir du haut. Comme `Execute`, un <xref:System.Activities.CompletionCallback> prend un <xref:System.Activities.NativeActivityContext>, en donnant à l'implémenteur l'accès à l'exécution.

 `MyWhile` diffère de `MySequence` dans le fait qu’il planifie un seul objet <xref:System.Activities.Activity> de façon répétée et qu’il utilise une <xref:System.Activities.Activity%601>< bool\> nommée `Condition` pour déterminer si cette planification doit avoir lieu. Comme `MySequence`, `MyWhile` utilise une méthode `InternalExecute` pour centraliser sa logique de planification. Il planifie le `Condition`<xref:System.Activities.Activity>< bool\> avec un <xref:System.Activities.CompletionCallback%601>\<bool > nommé `OnEvaluationCompleted`. Lorsque l'exécution de `Condition` est effectuée, son résultat devient disponible via ce <xref:System.Activities.CompletionCallback> dans un paramètre fortement typé nommé `result`. Si la valeur est `true`, `MyWhile` appelle  <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, en passant l'objet `Body`<xref:System.Activities.Activity> et `InternalExecute` comme <xref:System.Activities.CompletionCallback>. Lorsque l'exécution de `Body` est terminée, `Condition` est de nouveau planifié dans `InternalExecute`, en recommençant la boucle à zéro. Lorsque le `Condition` retourne la valeur `false`, une instance de `MyWhile` rend le contrôle à l'exécution sans planifier le `Body` et l'exécution le déplace dans l'état <xref:System.Activities.ActivityInstanceState.Closed>.

#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Ouvrez l’exemple de solution composite. sln dans Visual Studio 2010.

2. Générez et exécutez la solution.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
