---
title: Opérations de service (services de données WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: c254a7362c7bc28f4b38fc0189ae0ea763bc90cc
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568845"
---
# <a name="service-operations-wcf-data-services"></a>Opérations de service (services de données WCF)

WCF Data Services vous permet de définir des opérations de service sur un service de données pour exposer des méthodes sur le serveur. Comme d'autres ressources du service des données, les opérations de service sont adressées par les URI. Les opérations de service vous permettent d'exposer la logique métier dans un service de données, comme d'implémenter la logique de validation, pour appliquer la sécurité basée sur les rôles, ou exposer des fonctions d'interrogation spécialisées. Les opérations de service sont des méthodes ajoutées à la classe de service de données dérivée de <xref:System.Data.Services.DataService%601>. Comme pour toutes les autres ressources du service de données, vous pouvez fournir des paramètres à la méthode d'opération de service. Par exemple, l’URI d’opération de service suivant (basé sur le service de données de [démarrage rapide](quickstart-wcf-data-services.md) ) passe la valeur `London` au paramètre `city` :

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

La définition de cette opération de service est la suivante :

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

Vous pouvez utiliser la <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> du <xref:System.Data.Services.DataService%601> pour accéder directement à la source de données que le service de données utilise. Pour plus d’informations, consultez [Comment : définir une opération de service](how-to-define-a-service-operation-wcf-data-services.md).

Pour plus d’informations sur l’appel d’une opération de service à partir d’une application cliente .NET Framework, consultez [appel des opérations de service](calling-service-operations-wcf-data-services.md).

## <a name="service-operation-requirements"></a>Spécifications des opérations de service

Les spécifications suivantes s'appliquent lors de la définition d'opérations de service sur le service de données. Si une méthode ne respecte pas ces spécifications définies, elle ne sera pas exposée en tant qu'opération de service pour le service de données.

- L'opération doit être une méthode d'instance publique qui est un membre de la classe du service des données.

- La méthode d'opération peut accepter des paramètres d'entrée uniquement. Les données envoyées dans le corps du message ne sont pas accessibles par le service de données.

- Si des paramètres sont définis, le type de chaque paramètre doit être un type primitif. Toutes les données d'un type non primitif doivent être sérialisées et passées dans un paramètre de chaîne.

- La méthode doit retourner un des éléments suivants :

  - `void` (`Nothing` en Visual Basic)

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - Un type d'entité dans le modèle de données que le service des données expose. .

  - Une classe primitive telle qu'un entier ou une chaîne.

- Afin de prendre en charge les options de requêtes telles que le tri, la pagination et le filtrage, les méthodes d'opération de service doivent retourner <xref:System.Linq.IQueryable%601>. Les demande aux opérations de services qui incluent des options de requête sont rejetées pour les opérations qui retournent uniquement <xref:System.Collections.Generic.IEnumerable%601>.

- Afin de prendre en charge l'accès aux entités connexes à l'aide de propriétés de navigation, l'opération de service doit retourner <xref:System.Linq.IQueryable%601>.

- La méthode doit être annotée avec l’attribut `[WebGet]` ou `[WebInvoke]`.

  - `[WebGet]` permet d'appeler la méthode à l'aide d'une demande GET.

  - `[WebInvoke(Method = "POST")]` permet d'appeler la méthode à l'aide d'une demande POST. Les autres méthodes <xref:System.ServiceModel.Web.WebInvokeAttribute> ne sont pas prises en charge.

- Une opération de service peut être annotée avec le <xref:System.Data.Services.SingleResultAttribute>, qui spécifie que la valeur de retour de la méthode est une entité unique plutôt qu'une collection d'entités. Cette distinction détermine la sérialisation résultante de la réponse et le mode de représentation des parcours de propriété de navigation supplémentaires dans l'URI. Par exemple, lors de l'utilisation de la sérialisation AtomPub, une instance de type de ressource unique est représentée en tant qu'élément d'entrée et un jeu d'instances est représenté en tant qu'élément « feed ».

## <a name="addressing-service-operations"></a>Adressage d'opérations de service

Vous pouvez adresser des opérations de service en plaçant le nom de la méthode dans le premier segment de chemin d’accès d’un URI. Par exemple, l'URI suivant accède à une opération `GetOrdersByState` qui retourne une collection <xref:System.Linq.IQueryable%601> d'objets `Orders`.

```http
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

En appelant une opération de service, les paramètres sont fournis comme options de requête. L'opération de service précédente accepte un paramètre de chaîne `state` et une paramètre booléen `includeItems` qui indique s'il faut inclure les objets associés `Order_Detail` dans la réponse.

Voici les types de retour valides pour une opération de service :

|Types de retour valides|Règles d'URI|
|------------------------|---------------|
|`void` (`Nothing` en Visual Basic)<br /><br /> \- ou -<br /><br /> Types d'entité<br /><br /> \- ou -<br /><br /> Types primitifs|L’URI doit être un segment de chemin d’accès unique qui est le nom de l’opération de service. Les options de requête ne sont pas autorisées.|
|<xref:System.Collections.Generic.IEnumerable%601>|L’URI doit être un segment de chemin d’accès unique qui est le nom de l’opération de service. Comme le type de résultat n'est pas un type <xref:System.Linq.IQueryable%601>, les options de requête ne sont pas autorisées.|
|<xref:System.Linq.IQueryable%601>|Les segments de chemin d’accès, en plus du chemin d’accès qui est le nom de l’opération de service, sont autorisés. Les options de requête sont aussi autorisées.|

Des segments de chemin d'accès ou des options de requêtes supplémentaires peuvent être ajoutés à l'URI en fonction du type de retour de l'opération de service. Par exemple, l’URI suivant accède à une opération `GetOrdersByCity` qui retourne une collection <xref:System.Linq.IQueryable%601> d’objets `Orders`, classée par `RequiredDate` dans l’ordre décroissant, avec les objets `Order_Details` connexes :

```http
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a>Contrôle d'accès des opérations de service

La visibilité des opérations de service à l'échelle du service est contrôlée par la méthode <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> sur la classe <xref:System.Data.Services.IDataServiceConfiguration> d'une manière qui s'apparente au contrôle de la visibilité du jeu d'entités à l'aide de la méthode <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A>. Par exemple, la ligne de code suivante dans la définition du service de données permet l'accès à l'opération de service `CustomersByCity`.

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> Si une opération de service possède un type de retour qui est masqué en restreignant l’accès sur les jeux d’entités sous-jacents, l’opération de service ne sera pas disponible pour les applications clientes.

Pour plus d’informations, consultez [Comment : définir une opération de service](how-to-define-a-service-operation-wcf-data-services.md).

## <a name="raising-exceptions"></a>Déclenchement des exceptions

Nous vous recommandons d'utiliser la classe <xref:System.Data.Services.DataServiceException> chaque fois que vous déclenchez une exception dans l'exécution du service de données. Cela est dû fait que l'exécution du service de données sait mapper des propriétés de cet objet exception correctement au message de réponse HTTP. Lorsque vous déclenchez <xref:System.Data.Services.DataServiceException> dans une opération de service, l'exception renvoyée est encapsulée dans <xref:System.Reflection.TargetInvocationException>. Pour retourner la base <xref:System.Data.Services.DataServiceException> sans <xref:System.Reflection.TargetInvocationException>englobant, vous devez substituer la méthode <xref:System.Data.Services.DataService%601.HandleException%2A> dans <xref:System.Data.Services.DataService%601>, extraire<xref:System.Data.Services.DataServiceException> à partir de <xref:System.Reflection.TargetInvocationException>, et le retourner comme erreur de niveau supérieur, comme dans l'exemple suivant :

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a>Voir aussi

- [Intercepteurs](interceptors-wcf-data-services.md)
