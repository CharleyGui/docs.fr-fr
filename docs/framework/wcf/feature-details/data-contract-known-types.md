---
title: Types connus de contrats de données
description: Découvrez comment le modèle de contrat de données utilise la classe KnownTypeAttribute pour spécifier les types à inclure pendant la désérialisation dans WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 124083d86c220451c55a9290c2edf996b50d8d28
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286680"
---
# <a name="data-contract-known-types"></a>Types connus de contrats de données

La classe <xref:System.Runtime.Serialization.KnownTypeAttribute> vous permet de spécifier, en avance, les types qui doivent être inclus pour être pris en compte pendant la désérialisation. Pour obtenir un exemple fonctionnel, consultez l’exemple [Known Types](../samples/known-types.md) .  
  
 Normalement, lors du passage des paramètres et des valeurs de retour entre un client et un service, les deux points de terminaison partagent tous les contrats de données des données à transmettre. Toutefois, ce n'est pas le cas dans les circonstances suivantes :  
  
- Le contrat de données envoyé est dérivé du contrat de données attendu. Pour plus d’informations, consultez la section relative à l’héritage dans [équivalence des contrats de données](data-contract-equivalence.md). Dans ce cas, les données transmises n'ont pas le même contrat de données que celui attendu par le point de terminaison de réception.  
  
- Le type déclaré pour les informations à transmettre est une interface, par opposition à une classe, une structure ou une énumération. Par conséquent, il n'est pas possible de connaître à l'avance quel type implémentant l'interface est envoyé réellement et, par conséquent, le point de terminaison de réception ne peut pas déterminer, à l'avance, le contrat de données pour les données transmises.  
  
- Le type déclaré pour les informations à transmettre est <xref:System.Object>. Comme chaque type hérite de <xref:System.Object>, et il n'est pas possible de connaître à l'avance quel type est envoyé réellement, le point de terminaison de réception ne peut pas déterminer à l'avance le contrat de données pour les données transmises. Il s'agit d'un cas spécial du premier élément : chaque contrat de données dérive de la valeur par défaut, un contrat de données vierge généré pour <xref:System.Object>.  
  
- Certains types, y compris les types de .NET Framework, ont des membres qui se trouvent dans l’une des trois catégories précédentes. Par exemple, <xref:System.Collections.Hashtable> utilise <xref:System.Object> pour stocker les objets réels dans la table de hachage. Lors de la sérialisation de ces types, le côté réception ne peut pas déterminer à l'avance le contrat de données pour ces membres.  
  
## <a name="the-knowntypeattribute-class"></a>Classe KnownTypeAttribute  

 Lorsque les données arrivent à un point de terminaison de réception, le runtime WCF tente de désérialiser les données dans une instance d’un type de common language runtime (CLR). Le type instancié pour la désérialisation est choisi en inspectant d'abord le message entrant pour déterminer le contrat de données auquel le contenu du message se conforme. Le moteur de désérialisation essaie ensuite de rechercher un type CLR qui implémente un contrat de données compatible avec le contenu de message. Le jeu des types de candidat que le moteur de désérialisation autorise pendant ce processus porte le nom du jeu du désérialiseur des « types connus ».  
  
 Une façon d'informer le moteur de désérialisation d'un type est d'utiliser <xref:System.Runtime.Serialization.KnownTypeAttribute>. L'attribut ne peut pas être appliqué aux membres de données individuels, uniquement aux types de contrat de données entiers. L'attribut est appliqué à un *type externe* qui peut être une classe ou une structure. Dans son utilisation la plus simple, l'application de l'attribut spécifie un type en tant que « type connu ». Cela entraîne l'intégration du type connu dans un jeu de types connus à chaque fois qu'un objet du type externe ou tout objet référencé via ses membres est désérialisé. Plusieurs attributs <xref:System.Runtime.Serialization.KnownTypeAttribute> peuvent être appliqués au même type.  
  
## <a name="known-types-and-primitives"></a>Types et primitives connus  

 Les types primitifs, ainsi que certains types traités comme des primitives (par exemple, <xref:System.DateTime> et <xref:System.Xml.XmlElement>) sont toujours « connus » et il n'est jamais nécessaire de les ajouter par le biais de ce mécanisme. Cependant, les tableaux de types primitifs doivent être ajouté explicitement. La plupart des collections sont considérées comme équivalentes aux tableaux. (Les collections non génériques sont considérées comme équivalentes aux tableaux de <xref:System.Object>). Pour un exemple de l'utilisation des primitives, des tableaux de primitives et des collections de primitives, consultez l'exemple 4.  
  
> [!NOTE]
> Contrairement à d'autres types de primitive, la structure <xref:System.DateTimeOffset> n'est pas un type connu par défaut, donc elle doit être ajoutée manuellement à la liste de types connus.  
  
## <a name="examples"></a>Exemples  

 Voici quelques exemples de la classe <xref:System.Runtime.Serialization.KnownTypeAttribute> employée.  
  
#### <a name="example-1"></a>Exemple 1  

 Il existe trois classes avec une relation d'héritage.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 La classe `CompanyLogo` suivante peut être sérialisée, mais ne peut pas être désérialisée si le membre `ShapeOfLogo` a pour valeur un `CircleType` ou un objet `TriangleType` , étant donné que le moteur de désérialisation ne reconnaît pas de types avec les noms de contrat de données « Cercle » ou « Triangle ».  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 La méthode correcte pour écrire le type `CompanyLogo` est indiquée dans le code suivant.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Toutes les fois que le type `CompanyLogo2` externe est désérialisé, le moteur de désérialisation connaît `CircleType` et `TriangleType` et, par conséquent, est en mesure de rechercher des types correspondants pour les contrats de données « Cercle » ou « Triangle ».  
  
#### <a name="example-2"></a>Exemple 2  

 Dans l'exemple suivant, même si `CustomerTypeA` et `CustomerTypeB` ont le contrat de données `Customer` , une instance de `CustomerTypeB` est créée à chaque fois qu'un `PurchaseOrder` est désérialisé, car seul `CustomerTypeB` est connu du moteur de désérialisation.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Exemple 3  

 Dans l'exemple suivant, un <xref:System.Collections.Hashtable> stocke en interne son contenu sous la forme d'un <xref:System.Object>. Pour désérialiser une table de hachage correctement, le moteur de désérialisation doit connaître le jeu de types possibles qui peuvent se produire à cet endroit. Dans ce cas, nous savons à l'avance que seuls les objets `Book` et `Magazine` sont stockés dans le `Catalog`, par conséquent ils sont ajoutés à l'aide de l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute> .  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Exemple 4  

 Dans l'exemple suivant, un contrat de données stocke un nombre et une opération à effectuer sur le nombre. Le membre de données `Numbers` peut être un entier, un tableau d'entiers ou un objet <xref:System.Collections.Generic.List%601> qui contient des entiers.  
  
> [!CAUTION]
> Cela ne fonctionnera que du côté client si SVCUTIL.EXE est utilisé pour générer un proxy WCF. SVCUTIL.EXE récupère des métadonnées du service, notamment tous les types connus. Sans ces informations, un client ne sera pas en mesure de désérialiser les types.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Voici le code d'application.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Types, héritage et interfaces connus  

 Lorsqu'un type connu est associé à un type particulier à l'aide de l'attribut `KnownTypeAttribute` , le type connu est également associé à tous les types dérivés de ce type. Par exemple, consultez le code suivant.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 La classe `DoubleDrawing` ne requiert pas que l'attribut `KnownTypeAttribute` utilise `Square` et `Circle` dans le champ `AdditionalShape` , parce que la classe de base (`Drawing`) a déjà ces attributs appliqués.  
  
 Les types connus peuvent être associés uniquement à des classes et des structures, pas des interfaces.  
  
## <a name="known-types-using-open-generic-methods"></a>Types connus qui utilisent des méthodes génériques ouvertes  

 Il peut être nécessaire d'ajouter un type générique en tant que type connu. Toutefois, un type générique ouvert ne peut pas être passé en tant que paramètre à l'attribut `KnownTypeAttribute` .  
  
 Ce problème peut être résolu en utilisant un autre mécanisme : écrire une méthode qui retourne une liste de types à ajouter à la collection de types connus. Le nom de la méthode est spécifié comme un argument de chaîne à l'attribut `KnownTypeAttribute` en raison de certaines restrictions.  
  
 La méthode doit exister sur le type auquel l'attribut `KnownTypeAttribute` est appliqué, il doit être statique, il ne doit pas accepter de paramètres et doit retourner un objet qui peut être assigné à <xref:System.Collections.IEnumerable> de <xref:System.Type>.  
  
 Vous ne pouvez pas associer l'attribut `KnownTypeAttribute` avec un nom de méthode et des attributs `KnownTypeAttribute` avec des types réels sur le même type. En outre, vous ne pouvez pas appliquer plusieurs `KnownTypeAttribute` avec un nom de méthode au même type.  
  
 Consultez la classe suivante.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 Le champ `theDrawing` contient des instances d'une classe générique `ColorDrawing` et d'une classe générique `BlackAndWhiteDrawing`qui héritent toutes les deux d'une classe générique `Drawing`. Normalement, les deux doivent être ajoutées aux types connus, mais les éléments suivants ne sont pas une syntaxe valide pour des attributs.  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 Donc, une méthode doit être créée pour retourner ces types. La méthode correcte pour écrire ce type est indiquée dans le code suivant.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Méthodes supplémentaires pour ajouter des types connus  

 En outre, les types connus peuvent être ajoutés par le biais d'un fichier de configuration. Cela est utile lorsque vous ne contrôlez pas le type qui requiert des types connus pour une désérialisation appropriée, par exemple lors de l’utilisation de bibliothèques de types tiers avec Windows Communication Foundation (WCF).  
  
 Le fichier de configuration suivant indique comment spécifier un type connu dans un fichier de configuration.  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 Un type de contrat de données dans le fichier de configuration précédent appelé `MyCompany.Library.Shape` est déclaré comme ayant `MyCompany.Library.Circle` comme type connu.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [Known Types](../samples/known-types.md)
- [Équivalence de contrats de données](data-contract-equivalence.md)
- [Conception de contrats de service](../designing-service-contracts.md)
