---
title: Types connus de contrats de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 2ab0a41e87a9b14d1beac9fb0c39586f0ea16a4a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040197"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="7de92-102">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="7de92-102">Data Contract Known Types</span></span>
<span data-ttu-id="7de92-103">La classe <xref:System.Runtime.Serialization.KnownTypeAttribute> vous permet de spécifier, en avance, les types qui doivent être inclus pour être pris en compte pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="7de92-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="7de92-104">Pour obtenir un exemple fonctionnel, consultez l’exemple [Known Types](../../../../docs/framework/wcf/samples/known-types.md) .</span><span class="sxs-lookup"><span data-stu-id="7de92-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="7de92-105">Normalement, lors du passage des paramètres et des valeurs de retour entre un client et un service, les deux points de terminaison partagent tous les contrats de données des données à transmettre.</span><span class="sxs-lookup"><span data-stu-id="7de92-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="7de92-106">Toutefois, ce n'est pas le cas dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="7de92-106">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="7de92-107">Le contrat de données envoyé est dérivé du contrat de données attendu.</span><span class="sxs-lookup"><span data-stu-id="7de92-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="7de92-108">Pour plus d’informations, consultez la section relative à l’héritage dans [équivalence des contrats de données](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md).</span><span class="sxs-lookup"><span data-stu-id="7de92-108">For more information, see the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="7de92-109">Dans ce cas, les données transmises n'ont pas le même contrat de données que celui attendu par le point de terminaison de réception.</span><span class="sxs-lookup"><span data-stu-id="7de92-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="7de92-110">Le type déclaré pour les informations à transmettre est une interface, par opposition à une classe, une structure ou une énumération.</span><span class="sxs-lookup"><span data-stu-id="7de92-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="7de92-111">Par conséquent, il n'est pas possible de connaître à l'avance quel type implémentant l'interface est envoyé réellement et, par conséquent, le point de terminaison de réception ne peut pas déterminer, à l'avance, le contrat de données pour les données transmises.</span><span class="sxs-lookup"><span data-stu-id="7de92-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="7de92-112">Le type déclaré pour les informations à transmettre est <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="7de92-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="7de92-113">Comme chaque type hérite de <xref:System.Object>, et il n'est pas possible de connaître à l'avance quel type est envoyé réellement, le point de terminaison de réception ne peut pas déterminer à l'avance le contrat de données pour les données transmises.</span><span class="sxs-lookup"><span data-stu-id="7de92-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="7de92-114">Il s’agit d’un cas spécial du premier élément: Chaque contrat de données dérive de la valeur par défaut, un contrat de données vide <xref:System.Object>généré pour.</span><span class="sxs-lookup"><span data-stu-id="7de92-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="7de92-115">Certains types, y compris les types de .NET Framework, ont des membres qui se trouvent dans l’une des trois catégories précédentes.</span><span class="sxs-lookup"><span data-stu-id="7de92-115">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="7de92-116">Par exemple, <xref:System.Collections.Hashtable> utilise <xref:System.Object> pour stocker les objets réels dans la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="7de92-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="7de92-117">Lors de la sérialisation de ces types, le côté réception ne peut pas déterminer à l'avance le contrat de données pour ces membres.</span><span class="sxs-lookup"><span data-stu-id="7de92-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="7de92-118">Classe KnownTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="7de92-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="7de92-119">Lorsque les données arrivent à un point de terminaison de réception, le runtime WCF tente de désérialiser les données dans une instance d’un type de common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7de92-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="7de92-120">Le type instancié pour la désérialisation est choisi en inspectant d'abord le message entrant pour déterminer le contrat de données auquel le contenu du message se conforme.</span><span class="sxs-lookup"><span data-stu-id="7de92-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="7de92-121">Le moteur de désérialisation essaie ensuite de rechercher un type CLR qui implémente un contrat de données compatible avec le contenu de message.</span><span class="sxs-lookup"><span data-stu-id="7de92-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="7de92-122">Le jeu des types de candidat que le moteur de désérialisation autorise pendant ce processus porte le nom du jeu du désérialiseur des « types connus ».</span><span class="sxs-lookup"><span data-stu-id="7de92-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="7de92-123">Une façon d'informer le moteur de désérialisation d'un type est d'utiliser <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7de92-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="7de92-124">L'attribut ne peut pas être appliqué aux membres de données individuels, uniquement aux types de contrat de données entiers.</span><span class="sxs-lookup"><span data-stu-id="7de92-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="7de92-125">L'attribut est appliqué à un *type externe* qui peut être une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="7de92-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="7de92-126">Dans son utilisation la plus simple, l'application de l'attribut spécifie un type en tant que « type connu ».</span><span class="sxs-lookup"><span data-stu-id="7de92-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="7de92-127">Cela entraîne l'intégration du type connu dans un jeu de types connus à chaque fois qu'un objet du type externe ou tout objet référencé via ses membres est désérialisé.</span><span class="sxs-lookup"><span data-stu-id="7de92-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="7de92-128">Plusieurs attributs <xref:System.Runtime.Serialization.KnownTypeAttribute> peuvent être appliqués au même type.</span><span class="sxs-lookup"><span data-stu-id="7de92-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="7de92-129">Types et primitives connus</span><span class="sxs-lookup"><span data-stu-id="7de92-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="7de92-130">Les types primitifs, ainsi que certains types traités comme des primitives (par exemple, <xref:System.DateTime> et <xref:System.Xml.XmlElement>) sont toujours « connus » et il n'est jamais nécessaire de les ajouter par le biais de ce mécanisme.</span><span class="sxs-lookup"><span data-stu-id="7de92-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="7de92-131">Cependant, les tableaux de types primitifs doivent être ajouté explicitement.</span><span class="sxs-lookup"><span data-stu-id="7de92-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="7de92-132">La plupart des collections sont considérées comme équivalentes aux tableaux.</span><span class="sxs-lookup"><span data-stu-id="7de92-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="7de92-133">(Les collections non génériques sont considérées comme équivalentes aux tableaux de <xref:System.Object>).</span><span class="sxs-lookup"><span data-stu-id="7de92-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="7de92-134">Pour un exemple de l'utilisation des primitives, des tableaux de primitives et des collections de primitives, consultez l'exemple 4.</span><span class="sxs-lookup"><span data-stu-id="7de92-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7de92-135">Contrairement à d'autres types de primitive, la structure <xref:System.DateTimeOffset> n'est pas un type connu par défaut, donc elle doit être ajoutée manuellement à la liste de types connus.</span><span class="sxs-lookup"><span data-stu-id="7de92-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7de92-136">Exemples</span><span class="sxs-lookup"><span data-stu-id="7de92-136">Examples</span></span>  
 <span data-ttu-id="7de92-137">Voici quelques exemples de la classe <xref:System.Runtime.Serialization.KnownTypeAttribute> employée.</span><span class="sxs-lookup"><span data-stu-id="7de92-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="7de92-138">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="7de92-138">Example 1</span></span>  
 <span data-ttu-id="7de92-139">Il existe trois classes avec une relation d'héritage.</span><span class="sxs-lookup"><span data-stu-id="7de92-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="7de92-140">La classe `CompanyLogo` suivante peut être sérialisée, mais ne peut pas être désérialisée si le membre `ShapeOfLogo` a pour valeur un `CircleType` ou un objet `TriangleType` , étant donné que le moteur de désérialisation ne reconnaît pas de types avec les noms de contrat de données « Cercle » ou « Triangle ».</span><span class="sxs-lookup"><span data-stu-id="7de92-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="7de92-141">La méthode correcte pour écrire le type `CompanyLogo` est indiquée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7de92-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="7de92-142">Toutes les fois que le type `CompanyLogo2` externe est désérialisé, le moteur de désérialisation connaît `CircleType` et `TriangleType` et, par conséquent, est en mesure de rechercher des types correspondants pour les contrats de données « Cercle » ou « Triangle ».</span><span class="sxs-lookup"><span data-stu-id="7de92-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="7de92-143">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="7de92-143">Example 2</span></span>  
 <span data-ttu-id="7de92-144">Dans l'exemple suivant, même si `CustomerTypeA` et `CustomerTypeB` ont le contrat de données `Customer` , une instance de `CustomerTypeB` est créée à chaque fois qu'un `PurchaseOrder` est désérialisé, car seul `CustomerTypeB` est connu du moteur de désérialisation.</span><span class="sxs-lookup"><span data-stu-id="7de92-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="7de92-145">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="7de92-145">Example 3</span></span>  
 <span data-ttu-id="7de92-146">Dans l'exemple suivant, un <xref:System.Collections.Hashtable> stocke en interne son contenu sous la forme d'un <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="7de92-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="7de92-147">Pour désérialiser une table de hachage correctement, le moteur de désérialisation doit connaître le jeu de types possibles qui peuvent se produire à cet endroit.</span><span class="sxs-lookup"><span data-stu-id="7de92-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="7de92-148">Dans ce cas, nous savons à l'avance que seuls les objets `Book` et `Magazine` sont stockés dans le `Catalog`, par conséquent ils sont ajoutés à l'aide de l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="7de92-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="7de92-149">Exemple 4</span><span class="sxs-lookup"><span data-stu-id="7de92-149">Example 4</span></span>  
 <span data-ttu-id="7de92-150">Dans l'exemple suivant, un contrat de données stocke un nombre et une opération à effectuer sur le nombre.</span><span class="sxs-lookup"><span data-stu-id="7de92-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="7de92-151">Le membre de données `Numbers` peut être un entier, un tableau d'entiers ou un objet <xref:System.Collections.Generic.List%601> qui contient des entiers.</span><span class="sxs-lookup"><span data-stu-id="7de92-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7de92-152">Cela ne fonctionnera que du côté client si SVCUTIL.EXE est utilisé pour générer un proxy WCF.</span><span class="sxs-lookup"><span data-stu-id="7de92-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="7de92-153">SVCUTIL.EXE récupère des métadonnées du service, notamment tous les types connus.</span><span class="sxs-lookup"><span data-stu-id="7de92-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="7de92-154">Sans ces informations, un client ne sera pas en mesure de désérialiser les types.</span><span class="sxs-lookup"><span data-stu-id="7de92-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="7de92-155">Voici le code d'application.</span><span class="sxs-lookup"><span data-stu-id="7de92-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="7de92-156">Types, héritage et interfaces connus</span><span class="sxs-lookup"><span data-stu-id="7de92-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="7de92-157">Lorsqu'un type connu est associé à un type particulier à l'aide de l'attribut `KnownTypeAttribute` , le type connu est également associé à tous les types dérivés de ce type.</span><span class="sxs-lookup"><span data-stu-id="7de92-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="7de92-158">Par exemple, consultez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7de92-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="7de92-159">La classe `DoubleDrawing` ne requiert pas que l'attribut `KnownTypeAttribute` utilise `Square` et `Circle` dans le champ `AdditionalShape` , parce que la classe de base (`Drawing`) a déjà ces attributs appliqués.</span><span class="sxs-lookup"><span data-stu-id="7de92-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="7de92-160">Les types connus peuvent être associés uniquement à des classes et des structures, pas des interfaces.</span><span class="sxs-lookup"><span data-stu-id="7de92-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="7de92-161">Types connus qui utilisent des méthodes génériques ouvertes</span><span class="sxs-lookup"><span data-stu-id="7de92-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="7de92-162">Il peut être nécessaire d'ajouter un type générique en tant que type connu.</span><span class="sxs-lookup"><span data-stu-id="7de92-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="7de92-163">Toutefois, un type générique ouvert ne peut pas être passé en tant que paramètre à l'attribut `KnownTypeAttribute` .</span><span class="sxs-lookup"><span data-stu-id="7de92-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="7de92-164">Ce problème peut être résolu à l’aide d’un autre mécanisme: Écrivez une méthode qui retourne une liste de types à ajouter à la collection de types connus.</span><span class="sxs-lookup"><span data-stu-id="7de92-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="7de92-165">Le nom de la méthode est spécifié comme un argument de chaîne à l'attribut `KnownTypeAttribute` en raison de certaines restrictions.</span><span class="sxs-lookup"><span data-stu-id="7de92-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="7de92-166">La méthode doit exister sur le type auquel l'attribut `KnownTypeAttribute` est appliqué, il doit être statique, il ne doit pas accepter de paramètres et doit retourner un objet qui peut être assigné à <xref:System.Collections.IEnumerable> de <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="7de92-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="7de92-167">Vous ne pouvez pas associer l'attribut `KnownTypeAttribute` avec un nom de méthode et des attributs `KnownTypeAttribute` avec des types réels sur le même type.</span><span class="sxs-lookup"><span data-stu-id="7de92-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="7de92-168">En outre, vous ne pouvez pas appliquer plusieurs `KnownTypeAttribute` avec un nom de méthode au même type.</span><span class="sxs-lookup"><span data-stu-id="7de92-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="7de92-169">Consultez la classe suivante.</span><span class="sxs-lookup"><span data-stu-id="7de92-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="7de92-170">Le champ `theDrawing` contient des instances d'une classe générique `ColorDrawing` et d'une classe générique `BlackAndWhiteDrawing`qui héritent toutes les deux d'une classe générique `Drawing`.</span><span class="sxs-lookup"><span data-stu-id="7de92-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="7de92-171">Normalement, les deux doivent être ajoutées aux types connus, mais les éléments suivants ne sont pas une syntaxe valide pour des attributs.</span><span class="sxs-lookup"><span data-stu-id="7de92-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
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
  
 <span data-ttu-id="7de92-172">Donc, une méthode doit être créée pour retourner ces types.</span><span class="sxs-lookup"><span data-stu-id="7de92-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="7de92-173">La méthode correcte pour écrire ce type est indiquée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7de92-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="7de92-174">Méthodes supplémentaires pour ajouter des types connus</span><span class="sxs-lookup"><span data-stu-id="7de92-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="7de92-175">En outre, les types connus peuvent être ajoutés par le biais d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7de92-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="7de92-176">Cela est utile lorsque vous ne contrôlez pas le type qui requiert des types connus pour une désérialisation appropriée, par exemple lors de l’utilisation de bibliothèques de types tiers avec Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7de92-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="7de92-177">Le fichier de configuration suivant indique comment spécifier un type connu dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7de92-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="7de92-178">Un type de contrat de données dans le fichier de configuration précédent appelé `MyCompany.Library.Shape` est déclaré comme ayant `MyCompany.Library.Circle` comme type connu.</span><span class="sxs-lookup"><span data-stu-id="7de92-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de92-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7de92-179">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="7de92-180">Types connus</span><span class="sxs-lookup"><span data-stu-id="7de92-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)
- [<span data-ttu-id="7de92-181">Équivalence des contrats de données</span><span class="sxs-lookup"><span data-stu-id="7de92-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="7de92-182">Conception de contrats de service</span><span class="sxs-lookup"><span data-stu-id="7de92-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
