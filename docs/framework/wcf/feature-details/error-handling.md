---
title: Gestion des erreurs
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: 9c7d6814a6bf1189fd85de5eb440ec4a6840447e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539981"
---
# <a name="error-handling-in-windows-communication-foundation-wcf"></a>Gestion des erreurs dans les Windows Communication Foundation (WCF)

Lorsqu'un service rencontre une exception ou une erreur inattendue, il existe plusieurs manières de concevoir une solution de gestion des exceptions. Bien qu’il n’existe aucune solution de gestion des erreurs « correcte » ou « meilleure pratique », il existe plusieurs chemins valides à prendre en compte. Il est généralement recommandé d’implémenter une solution hybride qui associe plusieurs approches de la liste ci-dessous, en fonction de la complexité de l’implémentation WCF, du type et de la fréquence des exceptions, de la nature gérée et non gérée des exceptions, ainsi que des exigences de suivi, de journalisation ou de stratégie associées.

Ces solutions sont expliquées plus en détail dans le reste de cette section.

## <a name="the-microsoft-enterprise-library"></a>Microsoft Enterprise Library

Le bloc d’application de gestion des exceptions Microsoft Enterprise Library permet d’implémenter des modèles communs de conception et de créer une stratégie cohérente de traitement des exceptions qui se produisent dans toutes les couches de l’architecture d’une application d’entreprise. Il est conçu pour prendre en charge le code spécifique contenu dans les instructions catch des composants de l'application. Au lieu de répéter ce code (par exemple le code qui stocke les informations sur l'exception) dans des blocs catch identiques d'une application, le bloc d'application de gestion des exceptions permet aux développeurs d'encapsuler cette logique comme gestionnaires d'exceptions réutilisables.

Cette bibliothèque comprend un gestionnaire d'exceptions du contrat d'erreur prêt à l'emploi. Ce gestionnaire d’exceptions est conçu pour être utilisé dans les limites de service WCF et génère un nouveau contrat d’erreur à partir de l’exception.

Les blocs d'application visent à incorporer les meilleures pratiques fréquemment utilisées et à fournir une approche commune pour la gestion des exceptions dans votre application. D'autre part, les gestionnaires d'erreurs personnalisés et les contrats d'erreur développés s'avèrent également très utiles. Par exemple, les gestionnaires d'erreurs personnalisés offrent la possibilité de promouvoir automatiquement toutes les exceptions en FaultExceptions et également d'ajouter des fonctions d'enregistrement à votre application.

Pour plus d’informations, consultez [Microsoft Enterprise Library](/previous-versions/msp-n-p/ff632023(v=pandp.10)).

## <a name="dealing-with-expected-exceptions"></a>Traitement des exceptions attendues

La bonne marche à suivre consiste à intercepter les exceptions attendues dans chaque opération ou point d’extensibilité approprié, à déterminer si elles peuvent être récupérées à partir de et à retourner l’erreur personnalisée appropriée dans un FaultException \<T> .
  
## <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Traitement des exceptions inattendues à l’aide d’un IErrorHandler

Pour traiter les exceptions inattendues, il est recommandé de « raccorder » un IErrorHandler. Les gestionnaires d’erreurs interceptent uniquement les exceptions au niveau du runtime WCF (la couche « modèle de service »), et non au niveau de la couche du canal. La seule manière de connecter un IErrorHandler au niveau de canal consiste à créer un canal personnalisé, ce qui est déconseillé dans la plupart des scénarios.

Une « exception inattendue » n’est généralement ni une exception irrécupérable ni une exception de traitement ; au lieu de cela, il s’agit d’une exception d’utilisateur inattendue. Une exception irrécupérable (telle qu’une exception de mémoire insuffisante), généralement gérée automatiquement par le [Gestionnaire d’exceptions de modèle de service](xref:System.ServiceModel.Dispatcher.ExceptionHandler) , ne peut généralement pas être gérée correctement, et la seule raison de gérer une telle exception peut être d’effectuer une journalisation supplémentaire ou de retourner une exception standard au client. Une exception de traitement se produit dans le traitement du message (par exemple, au niveau de la sérialisation, de l'encodeur ou du formateur), généralement elle ne peut pas être gérée dans un IErrorHandler, car il est trop tôt ou trop tard pour que le gestionnaire d'erreurs intervienne lorsque ces exceptions se produisent. De même, les exceptions de transport ne peuvent pas être gérées dans un IErrorHandler.

Avec un IErrorHandler, vous pouvez explicitement contrôler le comportement de votre application lorsqu'une exception est levée. Ces options sont les suivantes :  

1. Décidez si vous souhaitez envoyer une erreur au client ou non.

2. Remplacez une exception par une erreur.

3. Remplacez une erreur par une autre erreur.

4. Effectuez la journalisation ou le suivi.

5. Exécuter d’autres activités personnalisées.

Pour installer un gestionnaire d'erreurs personnalisé, ajoutez-le à la propriété ErrorHandlers des répartiteurs de canal de votre service.  Il est possible d’avoir plusieurs gestionnaire d’erreurs et ils sont appelés dans l’ordre où ils sont ajoutés à cette collection.

IErrorHandler.ProvideFault contrôle le message d'erreur qui est envoyé au client. Cette méthode est appelée quel que soit le type de l'exception levée par une opération dans votre service. Si aucune opération n’est effectuée ici, WCF utilise son comportement par défaut et continue comme s’il n’existait aucun gestionnaire d’erreurs personnalisé en place.

Un domaine dans lequel vous pouvez adopter cette approche est lorsque vous souhaitez créer une place centrale de conversion des exceptions en erreurs avant qu'elles ne soient envoyées au client (en veillant à ce que l'instance ne soit pas supprimée et le canal déplacé vers l'état d'erreur).

La méthode IErrorHandler. HandleError est généralement utilisée pour implémenter des comportements liés aux erreurs, tels que la journalisation des erreurs, les notifications système, l’arrêt de l’application, etc. IErrorHandler. HandleError peut être appelé à plusieurs emplacements à l’intérieur du service et, en fonction de l’endroit où l’erreur est levée, la méthode HandleError peut ou non être appelée par le même thread que l’opération. aucune garantie n’est faite à cet égard.

## <a name="dealing-with-exceptions-outside-wcf"></a>Gestion des exceptions en dehors de WCF

Souvent, des exceptions de configuration, des exceptions de chaîne de connexion à la base de données, et d'autres exceptions similaires peuvent se produire dans le contexte d'une application WCF, mais elles ne sont pas des exceptions provoquées par le modèle de service ou le service Web. Ces exceptions sont des exceptions « normales » externes au service Web et doivent être traitées de la même façon que les autres exceptions externes de l’environnement doivent être gérées.

## <a name="tracing-exceptions"></a>Suivi d'exceptions

Le suivi est le seul emplacement « Catch-All » dans lequel il est possible de voir toutes les exceptions. Pour plus d'informations sur le suivi et l'enregistrement des exceptions, consultez Suivi et enregistrement.

## <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Erreurs de modèle d'URI lors de l'utilisation de WebGetAttribute et WebInvokeAttribute

Les attributs WebGet et WebInvoke vous permettent de spécifier un modèle d'URI qui mappe les composants de l'adresse de requête aux paramètres d'opération. Par exemple, le modèle d'URI « weather/{state}/{city} » mappe l'adresse de requête dans les jetons de littéraux, un état de paramètre nommé et un paramètre nommé city. Ces paramètres peuvent être liés par nom à certains des paramètres formels de l'opération.

Les paramètres de modèle s'affichent au format de chaînes dans l'URI et les paramètres formels d'un contrat typé peuvent être des types non-chaînes. Par conséquent, une conversion doit avoir lieu avant que l'opération puisse être appelée. Un [tableau de formats de conversion](wcf-web-http-programming-model-overview.md) est disponible.

Cependant, si la conversion échoue, il n'existe aucun moyen d'indiquer à l'opération qu'une erreur s'est produite. Conversion de type plutôt que de surfaces sous la forme d'un échec de distribution.

Une erreur de distribution de conversion de type peut être inspectée de la même façon que d'autres types d'erreurs de distribution en installant un gestionnaire d'erreurs. Le point d'extensibilité d'IErrorHandler est appelé pour gérer les exceptions au niveau de service. À partir de là, choisissez la réponse à renvoyer à l’appelant, et effectuez des tâches et des rapports personnalisés.

## <a name="see-also"></a>Voir aussi

- [Programmation WCF de base](../basic-wcf-programming.md)
