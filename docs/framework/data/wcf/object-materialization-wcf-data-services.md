---
title: Matérialisation d'objet (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: 68b04ac59d1b73d6e66a5a7836ce1bfe30d9c681
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975189"
---
# <a name="object-materialization-wcf-data-services"></a>Matérialisation d'objet (services de données WCF)

Lorsque vous utilisez la boîte de dialogue **Ajouter une référence de service** pour consommer un flux Open Data Protocol (OData) dans une application cliente basée sur .NET Framework, des classes de données équivalentes sont générées pour chaque type d’entité dans le modèle de données exposé par le flux. Pour plus d’informations, consultez [génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md). Les données d'entité retournées par une requête sont matérialisées dans une instance de l'une de ces classes de service de données client générées. Pour plus d’informations sur les options de fusion et la résolution d’identité pour les objets suivis, consultez [gestion du contexte du service de données](managing-the-data-service-context-wcf-data-services.md).

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet également de définir vos propres classes de service de données client plutôt que d'utiliser les classes de données générées par outil. Cela vous permet d'utiliser vos propres classes de données, également appelées classes de données POCO (plain-old CLR object). Lors de l’utilisation de ces types de classes de données personnalisées, vous devez attribuer à la classe de données la valeur <xref:System.Data.Services.Common.DataServiceKeyAttribute> ou <xref:System.Data.Services.Common.DataServiceEntityAttribute> et vous assurer que les noms de types sur le client correspondent aux noms de type dans le modèle de données du service de données.

Une fois que la bibliothèque a reçu le message de réponse de requête, elle matérialise les données retournées du flux OData dans des instances de classes de service de données client qui sont du type de la requête. Le processus général pour matérialiser ces objets est le suivant :

1. La bibliothèque cliente lit le type sérialisé de l'élément `entry` dans le flux du message de réponse et tente de créer une nouvelle instance du type correct, de l'une des manières suivantes :

    - Lorsque le type déclaré dans le flux a le même nom que le type <xref:System.Data.Services.Client.DataServiceQuery%601>, une nouvelle instance de ce type est créée à l'aide du constructeur vide.

    - Lorsque le type déclaré dans le flux a le même nom qu'un type dérivé du type <xref:System.Data.Services.Client.DataServiceQuery%601>, une nouvelle instance de ce type dérivé est créée à l'aide du constructeur vide.

    - Lorsque le type déclaré dans le flux ne correspond pas au type <xref:System.Data.Services.Client.DataServiceQuery%601> ou à tout type dérivé, une nouvelle instance du type demandé est créée à l'aide du constructeur vide.

    - Lorsque la propriété <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> est définie, le délégué fourni est appelé pour remplacer le mappage du type basé sur le nom par défaut et une nouvelle instance du type retourné par <xref:System.Func%602> est créée à la place. Si ce délégué retourne une valeur Null, une nouvelle instance du type demandé est créée à la place. Il se peut que vous deviez remplacer le mappage du nom du type basé sur le nom par défaut qui prend en charge les scénarios d'héritage.

2. La bibliothèque cliente lit la valeur URI de l'élément `id` de `entry`, qui est la valeur d'identité de l'entité. À moins qu'une valeur <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> de <xref:System.Data.Services.Client.MergeOption.NoTracking> soit utilisée, la valeur d'identité est utilisée pour suivre l'objet dans <xref:System.Data.Services.Client.DataServiceContext>. La valeur d'identité est également utilisée pour garantir que seule une instance d'entité est créée, même lorsqu'une entité est retournée plusieurs fois dans la réponse à la requête.

3. La bibliothèque cliente lit les propriétés de l'entrée de flux et définit les propriétés correspondantes sur l'objet créé. Lorsqu'un objet qui a la même valeur d'identité existe déjà dans <xref:System.Data.Services.Client.DataServiceContext>, les propriétés sont définies selon le paramètre <xref:System.Data.Services.Client.MergeOption> de <xref:System.Data.Services.Client.DataServiceContext>. La réponse peut contenir des valeurs de propriété qui n'ont pas de propriété correspondante dans le type de client. Dans ce cas, l'action dépend de la valeur de la propriété <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> de <xref:System.Data.Services.Client.DataServiceContext>. Lorsque cette propriété est définie sur `true`, la propriété manquante est ignorée. Sinon, une erreur est générée. Les propriétés sont définies comme suit :

    - Les propriétés scalaires sont définies sur la valeur correspondante dans l'entrée dans le message de réponse.

    - Les propriétés complexes sont définies sur une nouvelle instance de type complexe, définie avec les propriétés du type complexe de la réponse.

    - Les propriétés de navigation qui retournent une collection d’entités associées sont définies sur une instance nouvelle ou existante de <xref:System.Collections.Generic.ICollection%601>, où `T` est le type d’entité associée. Cette collection est vide à moins que les objets connexes aient été chargés dans <xref:System.Data.Services.Client.DataServiceContext>. Pour plus d’informations, consultez chargement d’un [contenu différé](loading-deferred-content-wcf-data-services.md).

      > [!NOTE]
      > Lorsque les classes de données clientes générées prennent en charge la liaison de données, les propriétés de navigation retournent des instances de la classe <xref:System.Data.Services.Client.DataServiceCollection%601> à la place. Pour plus d’informations, consultez [liaison de données à des contrôles](binding-data-to-controls-wcf-data-services.md).

4. L'événement <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> est déclenché.

5. La bibliothèque cliente joint l'objet à <xref:System.Data.Services.Client.DataServiceContext>. L'objet n'est pas joint quand <xref:System.Data.Services.Client.MergeOption> est <xref:System.Data.Services.Client.MergeOption.NoTracking>.

## <a name="see-also"></a>Voir aussi

- [Interrogation du service de données](querying-the-data-service-wcf-data-services.md)
- [Projections de requête](query-projections-wcf-data-services.md)
