---
title: Portée et visibilité de la définition de l'activité
ms.date: 03/30/2017
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
ms.openlocfilehash: c7f656fee4960a8c43ac58abafba400ed9b35bc1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289163"
---
# <a name="activity-definition-scoping-and-visibility"></a>Portée et visibilité de la définition de l'activité

La portée et la visibilité de la définition d'une activité, tout comme la portée et la visibilité d'un objet représentent la capacité d'autres objets d'accéder aux membres de l'activité. La définition de l'activité est assurée par les implémentations suivantes :  
  
1. Détermination des membres (objets <xref:System.Activities.Argument>, <xref:System.Activities.Variable> et <xref:System.Activities.ActivityDelegate>, et activités enfants) qu'une activité expose aux utilisateurs.  
  
2. Implémentation de la logique d'exécution de l'activité  
  
 L'implémentation peut impliquer des membres qui ne sont pas exposés aux consommateurs de l'activité, mais qui sont des détails de l'implémentation.  Semblalble à la définition de type, le modèle d'activité permet à un auteur de qualifier la visibilité d'un membre d'activité concernant la définition de l'activité définie.  La visibilité définit les aspects de l'utilisation de membre, notamment la portée des données.  
  
## <a name="scope"></a>Étendue  

 Outre la portée des données, la visibilité du modèle d’activité peut limiter l’accès à d’autres aspects de l’activité, tels que la validation, le débogage, le suivi ou le traçage. Les propriétés d'exécution utilisent la visibilité et la portée pour contraindre les caractéristiques d'exécution à une portée spécifique de définition. Les racines secondaires utilisent la visibilité et la portée pour contraindre l'état capturé par un <xref:System.Activities.Statements.CompensableActivity> à la portée de la définition dans laquelle les activités compensables sont utilisées.  
  
## <a name="definition-and-usage"></a>Définition et utilisation  

 Un flux de travail est écrit en créant de nouvelles activités en héritant des classes d’activité de base et en utilisant des activités de la [bibliothèque d’activités intégrée](net-framework-4-5-built-in-activity-library.md). Pour utiliser une activité, l'auteur de l'activité doit configurer la visibilité de chaque composant de sa définition.  
  
### <a name="activity-members"></a>Membres d'activité  

 Le modèle d’activité définit les arguments, les variables, les délégués et les activités enfants que l’activité rend disponible aux consommateurs. Chacun de ces membres peut être déclaré `public` ou `private`. Les membres publics sont configurés par le consommateur de l'activité, alors que les membres `private` utilisent une implémentation corrigée par l'auteur de l'activité. Les règles de visibilité applicables à la portée des données sont les suivantes :  
  
1. Les membres publics et les membres publics d'activités enfants publiques peuvent référencer des variables publiques.  
  
2. Les membres privés et les membres publics d'activités enfants publiques peuvent référencer des arguments et des variables privées.  
  
 Un membre pouvant être défini par le consommateur d'une activité ne doit jamais être rendu privé.  
  
### <a name="authoring-models"></a>Création de modèles  

 Les activités personnalisées sont définies à l'aide de <xref:System.Activities.NativeActivity>, <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity> ou <xref:System.Activities.AsyncCodeActivity>. Les activités dérivées de ces classes peuvent exposer des types de membres différents avec différentes visibilités.  
  
#### <a name="nativeactivity"></a>NativeActivity  

 Les activités dérivant de <xref:System.Activities.NativeActivity> ont un comportement qui est écrit dans le code impératif, et peuvent éventuellement être définies à l'aide d'activités existantes. La dérivation des activités de <xref:System.Activities.NativeActivity> accorde l’accès à l’ensemble des fonctionnalités exposées par le runtime. Tout membre d'une telle activité peut être défini à l'aide de la visibilité publique ou privée, à l'exception des arguments, qui peuvent uniquement être déclarés `public`.  
  
 Les membres de classes dérivées de <xref:System.Activities.NativeActivity> sont déclarés au runtime à l'aide du struct <xref:System.Activities.NativeActivityMetadata> passé à la méthode <xref:System.Activities.NativeActivity.CacheMetadata%2A>.  
  
#### <a name="activity"></a>Activité  

 Les activités créées à l'aide de <xref:System.Activities.Activity> ont un comportement qui est conçu strictement via la composition d'autres activités. La classe <xref:System.Activities.Activity> a une implémentation de l'activité enfant, obtenue par le runtime à l'aide de <xref:System.Activities.Activity.Implementation%2A>. Une activité dérivant de <xref:System.Activities.Activity> peut définir des arguments publics, des variables publiques, des ActivityDelegates et des activités importés.  
  
 Les ActivityDelegates et les activités importés sont déclarés en tant qu'enfants publics de l'activité, mais ne peuvent pas être planifiés directement par l'activité. Ces informations sont utilisées lors de la validation pour éviter d'exécuter des validations de parents dans des emplacements où l'activité ne sera jamais exécutée. Les enfants importés, comme les enfants publics, peuvent être référencés et planifiés par l'implémentation de l'activité. Cela signifie qu'une activité qui importe une activité nommée Activity1 peut contenir un <xref:System.Activities.Statements.Sequence> dans son implémentation qui planifie Activity1.  
  
#### <a name="codeactivity-asynccodeactivity"></a>CodeActivity/AsyncCodeActivity  

 Cette classe de base est utilisée pour la création de comportement en code impératif. Les activités qui dérivent de cette classe ont uniquement accès aux arguments qu’elles exposent. En d’autres termes, seuls les membres pouvant être exposés par ces activités sont des arguments publics. Aucun autre membre ou visibilité ne s'applique à ces activités.  
  
#### <a name="summary-of-visibilities"></a>Résumé des visibilités  

 Le tableau suivant récapitule les informations de cette rubrique.  
  
|Type de membre|NativeActivity|Activité|CodeActivity/AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|Arguments|Public/ Private|Public|Non applicable|  
|Variables|Public/ Private|Public|Non applicable|  
|Activités enfants|Public/ Private|Public, un enfant privé corrigé défini dans l'implémentation.|Non applicable|  
|ActivityDelegates|Public/ Private|Public|Non applicable|  
  
 En général, un membre ne pouvant pas être défini par le consomamteur d'une activité ne doit jamais être rendu public.  
  
### <a name="execution-properties"></a>Propriétés d'exécution  

 Dans certains scénarios, il s'avère utile de définir la portée d'une propriété d'exécution spécifique aux enfants publics d'une activité. La collection <xref:System.Activities.ExecutionProperties> offre cette possibilité avec la méthode <xref:System.Activities.ExecutionProperties.Add%2A>. Cette méthode a un paramètre Boolean indiquant si la portée d'une propriété spécifique est tous les enfants ou uniquement ceux qui sont publics. Si ce paramètre a la valeur `true`, la propriété sera uniquement visible aux membres publics de leurs enfants publics.  
  
### <a name="secondary-roots"></a>Racines secondaires  

 Une racine secondaire correspond au mécanisme interne de gestion de l'état des activités de compensation. Lorsque l'exécution d'un <xref:System.Activities.Statements.CompensableActivity> est terminée, son état n'est pas nettoyé immédiatement. L'état est conservé par le runtime dans une racine secondaire jusqu'à ce que l'épisode de compensation soit terminé. Les environnements d'emplacement capturés avec la racine secondaire correspondent à la portée de la définition dans laquelle l'activité Compensable est utilisée.
