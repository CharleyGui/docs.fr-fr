---
title: Sérialisation et métadonnées
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: cc9adf0e6627ef3190e74fea5d4f0f3afd581811
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389229"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="cc2f0-102">Sérialisation et métadonnées</span><span class="sxs-lookup"><span data-stu-id="cc2f0-102">Serialization and Metadata</span></span>

<span data-ttu-id="cc2f0-103">Si votre application sérialise et désérialise des objets, vous devrez peut-être ajouter des entrées à votre fichier de directives runtime (.rd.xml) pour que les métadonnées nécessaires soient présentes au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="cc2f0-104">Il existe deux catégories de sérialiseurs et chacune nécessite un traitement différent dans votre fichier de directives runtime :</span><span class="sxs-lookup"><span data-stu-id="cc2f0-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="cc2f0-105">Sérialiseurs tiers basés sur la réflexion.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="cc2f0-106">Ils nécessitent des modifications dans votre fichier de directives runtime et sont décrits dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="cc2f0-107">Sérialisateurs non-réflexion-basés trouvés dans la bibliothèque de classe cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-107">Non-reflection-based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="cc2f0-108">Ceux-ci peuvent nécessiter des modifications dans votre fichier de directives runtime et sont décrits dans la section [Sérialiseurs Microsoft](#Microsoft).</span><span class="sxs-lookup"><span data-stu-id="cc2f0-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="cc2f0-109">Sérialiseurs tiers</span><span class="sxs-lookup"><span data-stu-id="cc2f0-109">Third-party serializers</span></span>

 <span data-ttu-id="cc2f0-110">Les sérialiseurs tiers, y compris Newtonsoft.JSON, sont généralement basés sur la réflexion.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="cc2f0-111">Avec un objet BLOB (Binary Large Object) de données sérialisées, les champs de données sont affectés à un type concret en fonction des noms des champs du type cible.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="cc2f0-112">L’utilisation de ces bibliothèques entraîne au minimum des exceptions [MissingMetadataException](missingmetadataexception-class-net-native.md) pour chaque objet <xref:System.Type> que vous essayez de sérialiser ou de désérialiser dans une collection `List<Type>`.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-112">At a minimum, using these libraries causes [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="cc2f0-113">La façon la plus simple de résoudre les problèmes causés par les métadonnées manquantes pour ces sérialiseurs consiste à collecter les types qui seront utilisés dans la sérialisation dans un espace de noms unique (tel que `App.Models`) et à lui appliquer une directive de métadonnées `Serialize` :</span><span class="sxs-lookup"><span data-stu-id="cc2f0-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="cc2f0-114">Pour plus d’informations sur la syntaxe utilisée dans l’exemple, voir [ \<Namespace> Element](namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="cc2f0-114">For information about the syntax used in the example, see [\<Namespace> Element](namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="cc2f0-115">Sérialiseurs Microsoft</span><span class="sxs-lookup"><span data-stu-id="cc2f0-115">Microsoft serializers</span></span>

 <span data-ttu-id="cc2f0-116">Bien que les classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et <xref:System.Xml.Serialization.XmlSerializer> ne reposent pas sur la réflexion, elles nécessitent la génération de code en fonction de l'objet à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="cc2f0-117">Les constructeurs surchargés pour chaque sérialiseur incluent un paramètre <xref:System.Type> qui spécifie le type à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="cc2f0-118">La façon dont vous spécifiez ce type dans votre code définit l'action à entreprendre, comme indiqué dans les deux sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="cc2f0-119">typeof utilisé dans le constructeur</span><span class="sxs-lookup"><span data-stu-id="cc2f0-119">typeof used in the constructor</span></span>

 <span data-ttu-id="cc2f0-120">Si vous appelez un constructeur de ces classes de sérialisation et que vous incluez l’opérateur [de type Cmd](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) dans l’appel de méthode, **vous n’avez pas à effectuer de travail supplémentaire.**</span><span class="sxs-lookup"><span data-stu-id="cc2f0-120">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="cc2f0-121">Par exemple, dans chacun des appels suivants d'un constructeur de classe de sérialisation, le mot clé `typeof` est utilisé dans le cadre de l'expression passée au constructeur.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="cc2f0-122">Le compilateur .NET Native gérera automatiquement ce code.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="cc2f0-123">typeof utilisé à l'extérieur du constructeur</span><span class="sxs-lookup"><span data-stu-id="cc2f0-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="cc2f0-124">Si vous appelez un constructeur de ces classes de sérialisation et utilisez l’opérateur <xref:System.Type> de type [Cmd](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) en dehors de l’expression fournie au paramètre du constructeur, comme dans le code suivant, le compilateur natif .NET ne peut pas résoudre le type :</span><span class="sxs-lookup"><span data-stu-id="cc2f0-124">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="cc2f0-125">Dans ce cas, vous devez spécifier le type dans le fichier de directives runtime en ajoutant une entrée comme suit :</span><span class="sxs-lookup"><span data-stu-id="cc2f0-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="cc2f0-126">De même, si vous appelez <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> un constructeur tel <xref:System.Type> que et fournissez une gamme d’objets supplémentaires pour sérialiser, comme dans le code suivant, le compilateur natif .NET ne peut pas résoudre ces types.</span><span class="sxs-lookup"><span data-stu-id="cc2f0-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
<span data-ttu-id="cc2f0-127">Ajoutez des entrées telles que les suivantes pour chaque type au fichier des directives d’exécution :</span><span class="sxs-lookup"><span data-stu-id="cc2f0-127">Add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
<span data-ttu-id="cc2f0-128">Pour plus d’informations sur la [ \<](type-element-net-native.md)syntaxe utilisée dans l’exemple, voir Type> Element .</span><span class="sxs-lookup"><span data-stu-id="cc2f0-128">For information about the syntax used in the example, see [\<Type> Element](type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc2f0-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc2f0-129">See also</span></span>

- [<span data-ttu-id="cc2f0-130">Informations de référence sur le fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="cc2f0-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="cc2f0-131">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="cc2f0-131">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="cc2f0-132">\<Type> Élément</span><span class="sxs-lookup"><span data-stu-id="cc2f0-132">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="cc2f0-133">\<Article de> Namespace</span><span class="sxs-lookup"><span data-stu-id="cc2f0-133">\<Namespace> Element</span></span>](namespace-element-net-native.md)
