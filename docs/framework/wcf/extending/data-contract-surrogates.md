---
title: Substituts de contrats de données
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: e33a487c03bbf87666d517040e00131f5482be6f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251514"
---
# <a name="data-contract-surrogates"></a>Substituts de contrats de données

Le *substitut* de contrat de données est une fonctionnalité avancée basée sur le modèle de contrat de données. Cette fonctionnalité est destinée à la personnalisation et à la substitution de type dans les situations où les utilisateurs souhaitent changer la manière dont un type est sérialisé, désérialisé ou projeté dans des métadonnées. On peut par exemple utiliser un substitut lorsque aucun contrat de données n'a été spécifié pour le type, que les champs et propriétés ne sont pas marqués avec l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> ou que les utilisateurs souhaitent créer des variations de schéma de manière dynamique.  
  
 La sérialisation et la désérialisation sont accomplies avec le substitut de contrat de données lors de l’utilisation de <xref:System.Runtime.Serialization.DataContractSerializer> pour effectuer la conversion à partir du .NET Framework vers un format approprié, tel que XML. Le substitut de contrat de données peut également être utilisé pour modifier les métadonnées exportées pour les types, lors de la production de représentations de métadonnées telles que des documents XSD (XML Schema Documents). Lors de l'importation, le code est créé à partir des métadonnées et le substitut peut être utilisé dans ce cas pour personnaliser également le code généré.  
  
## <a name="how-the-surrogate-works"></a>Fonctionnement du substitut  

 Un substitut mappe un type (le type « d'origine ») à un autre type (le type « substitué »). L'exemple suivant illustre le type `Inventory` d'origine et un nouveau type `InventorySurrogated` de substitution. Le type `Inventory` n'est pas sérialisable, mais le type `InventorySurrogated` l'est :  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Aucun contrat de données n'ayant été défini pour cette classe, vous devez convertir la classe en une classe de substitution avec un contrat de données. La classe de substitution est illustrée dans l'exemple suivant :  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Implémentation de l'IDataContractSurrogate  

 Pour utiliser le substitut de contrat de données, implémentez l'interface <xref:System.Runtime.Serialization.IDataContractSurrogate>.  
  
 Vous trouverez ci-dessous une vue d'ensemble de chaque méthode de <xref:System.Runtime.Serialization.IDataContractSurrogate> avec une implémentation possible.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  

 La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> établit une correspondance entre les types. Cette méthode est requise pour la sérialisation, la désérialisation, l'importation et l'exportation.  
  
 La première tâche consiste à définir les types qui seront mappés à d'autres types. Par exemple :  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
- Lors de la sérialisation, le mappage retourné par cette méthode est utilisé par la suite pour transformer l'instance d'origine en une instance de substitution en appelant la méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A>.  
  
- Lors de la désérialisation, le mappage retourné par cette méthode est utilisé par le sérialiseur afin de désérialiser en une instance du type de substitution. La méthode appelle par la suite <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> pour transformer l'instance substituée en une instance du type d'origine.  
  
- Lors de l'exportation, le type de substitution retourné par cette méthode est reflété afin d'obtenir le contrat de données à utiliser pour générer les métadonnées.  
  
- Lors de l'importation, le type initial est modifié en un type de substitution qui est reflété afin d'obtenir le contrat de données à utiliser à des fins telles que le référencement de prise en charge.  
  
 Le paramètre <xref:System.Type> est le type de l'objet sérialisé, désérialisé, importé ou exporté. La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> doit retourner le type d'entrée si le substitut ne gère pas le type. Autrement, retournez le type substitué approprié. S'il existe plusieurs types de substitution, de nombreux mappages peuvent être définis dans cette méthode.  
  
 La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> n'est pas appelée pour les primitives de contrat de données intégrées, telles que <xref:System.Int32> ou <xref:System.String>. Pour d'autres types, tels que les tableaux, les types définis par l'utilisateur et autres structures de données, cette méthode sera appelée pour chaque type.  
  
 Dans l'exemple précédent, la méthode vérifie si les paramètres `type` et `Inventory` sont comparables. Si c'est le cas, la méthode le mappe à `InventorySurrogated`. Chaque fois qu’une sérialisation, une désérialisation, un schéma d’importation ou un schéma d’exportation est appelé(e), cette fonction est appelée en premier afin de déterminer le mappage entre les types.  
  
### <a name="getobjecttoserialize-method"></a>Méthode GetObjectToSerialize  

 La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> convertit l'instance de type d'origine en instance de type substitué. La méthode est requise pour la sérialisation.  
  
 L'étape suivante consiste à définir la façon dont les données physiques seront mappées de l'instance d'origine au substitut en implémentant la méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A>. Par exemple :  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> est appelée lorsqu'un objet est sérialisé. Cette méthode transfère des données du type d'origine aux champs du type substitué. Les champs peuvent être mappés directement à des champs de substitution, ou des manipulations des données d'origine peuvent être stockées dans le substitut. Certaines utilisations possibles incluent : mappage direct des champs, exécution d'opérations sur les données à stocker dans les champs substitués, ou stockage du XML du type d'origine dans le champ substitué.  
  
 Le paramètre `targetType` fait référence au type déclaré du membre. Ce paramètre est le type substitué retourné par la méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A>. Le sérialiseur n'applique pas l'impératif selon lequel l'objet retourné doit être assignable à ce type. Le `obj` paramètre est l’objet à sérialiser et est converti en son substitut, si nécessaire. Cette méthode doit retourner l'objet d'entrée si le substitué ne gère pas l'objet. Autrement, le nouvel objet de substitution sera retourné. Le substitut n'est pas appelé si l'objet est null. Plusieurs mappages de substitution pour différentes instances peuvent être définis dans cette méthode.  
  
 Lorsque vous créez un <xref:System.Runtime.Serialization.DataContractSerializer>, vous pouvez faire en sorte qu'il conserve les références d'objets. (Pour plus d’informations, consultez [sérialisation et désérialisation](../feature-details/serialization-and-deserialization.md).) Pour ce faire, affectez au `preserveObjectReferences` paramètre dans son constructeur la valeur `true` . Dans ce cas, le substitut est appelé une seule fois pour un objet puisque toutes les sérialisations suivantes écrivent simplement la référence dans le flux. Si `preserveObjectReferences` a la valeur `false`, le substitut est appelé chaque fois qu'une instance est rencontrée.  
  
 Si le type de l'instance sérialisé diffère du type déclaré, les informations de type sont écrites dans le flux, par exemple `xsi:type` pour autoriser l'instance à être désérialisée à l'autre extrémité. Ce processus se produit que l'objet soit substitué ou non.  
  
 L'exemple ci-dessus convertit les données de l'instance `Inventory` en données `InventorySurrogated`. Il vérifie le type de l'objet et effectue les manipulations nécessaires pour effectuer la conversion au type substitué. Dans ce cas, les champs de la classe `Inventory` sont copiés directement vers les champs de la classe `InventorySurrogated`.  
  
### <a name="getdeserializedobject-method"></a>Méthode GetDeserializedObject  

 La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> convertit l'instance de type substitué en instance de type d'origine. Elle est requise pour la désérialisation.  
  
 La tâche suivante consiste à définir la façon dont les données physiques seront mappées de l’instance de substitution à l’original. Par exemple :  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Cette méthode est appelée uniquement pendant la désérialisation d'un objet. Elle fournit un mappage de données inverse pour la désérialisation du type de substitution à son type d'origine. Elle est semblable à la méthode `GetObjectToSerialize`, et on peut l'utiliser afin d'échanger directement des données de champs, effectuer des opérations sur les données et stocker des données XML. Lors de la désérialisation, vous risquez de ne pas toujours obtenir les valeurs de données exactes de l'original en raison des manipulations liées à la conversion des données.  
  
 Le paramètre `targetType` fait référence au type déclaré du membre. Ce paramètre est le type substitué retourné par la méthode `GetDataContractType`. Le `obj` paramètre fait référence à l’objet qui a été désérialisé. L'objet peut être reconverti en son type d'origine s'il est substitué. Cette méthode retourne l'objet d'entrée si le substitue ne gère pas l'objet. Autrement, l'objet désérialisé sera retourné une fois sa conversion achevée. S'il existe plusieurs types de substitution, vous pouvez fournir la conversion de données du type de substitution au type principal pour chacun d'entre eux en indiquant chaque type et sa conversion.  
  
 Lors du retour d'un objet, les tables d'objets internes sont mises à jour avec l'objet retourné par ce substitut. Toute référence ultérieure à une instance obtiendra l'instance substituée à partir des tables d'objets.  
  
 L'exemple précédent reconvertit des objets de type `InventorySurrogated` en type `Inventory` initial. Dans ce cas, les données sont retransférées directement à partir de `InventorySurrogated` vers ses champs correspondants dans `Inventory`. Étant donné qu'il n'y a pas de manipulations de données, chacun des champs membres contiendra les mêmes valeurs qu'avant la sérialisation.  
  
### <a name="getcustomdatatoexport-method"></a>Méthode GetCustomDataToExport  

 Lors de l'exportation d'un schéma, la méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> est facultative. Elle est utilisée pour insérer des conseils ou des données supplémentaires dans le schéma exporté. Les données supplémentaires peuvent être insérées au niveau du membre ou au niveau du type. Par exemple :  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Cette méthode (avec deux surcharges) autorise l'inclusion d'informations supplémentaires dans les métadonnées au niveau du membre ou au niveau du type. Il est possible d'inclure des conseils relatifs au caractère public ou privé d'un membre et des commentaires qui seraient conservés durant toute l'exportation et l'importation du schéma. De telles informations seraient perdues sans cette méthode. Cette méthode ne provoque pas l'insertion ou la suppression de membres ou de types, mais elle ajoute plutôt des données supplémentaires aux schémas à l'un ou l'autre de ces niveaux.  
  
 La méthode est surchargée et peut prendre un `Type` (paramètre `clrtype`) ou un <xref:System.Reflection.MemberInfo> (paramètre `memberInfo`). Le deuxième paramètre est toujours un `Type` (paramètre `dataContractType`). Cette méthode est appelée pour chaque membre et type du type `dataContractType` substitué.  
  
 L'une ou l'autre de ces surcharges doit retourner `null` ou un objet sérialisable. Un objet non null sera sérialisé comme annotation dans le schéma exporté. Pour la surcharge `Type`, chaque type exporté vers le schéma est envoyé à cette méthode dans le premier paramètre avec le type substitué comme paramètre `dataContractType`. Pour la surcharge `MemberInfo`, chaque membre exporté vers le schéma envoie ses informations comme paramètre `memberInfo` avec le type substitué dans le deuxième paramètre.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>Méthode GetCustomDataToExport (Type, Type)  

 La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> est appelée pendant l'exportation de schéma pour chaque définition de type. La méthode ajoute des informations aux types dans le schéma lors de l'exportation. Chaque type défini est envoyé à cette méthode pour déterminer si des données supplémentaires doivent être incluses dans le schéma.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>Méthode GetCustomDataToExport (MemberInfo, Type)  

 Le <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> est appelé pendant l'exportation pour chaque membre dans les types exportés. Cette fonction vous permet de personnaliser tout commentaire pour les membres qui seront inclus dans le schéma lors de l'exportation. Les informations pour chaque membre dans la classe sont envoyées à cette méthode afin de vérifier si des données supplémentaires doivent être ajoutées dans le schéma.  
  
 L'exemple suivant recherche dans le `dataContractType` pour chaque membre du substitut. Il retourne ensuite le modificateur d’accès approprié pour chaque champ. Sans cette personnalisation, la valeur par défaut pour les modificateurs d’accès est publique. Par conséquent, tous les membres seraient définis comme publics dans le code généré à l'aide du schéma exporté, quelles que soient leurs restrictions d'accès réelles. Si cette implémentation n'était pas utilisée, le membre `numpens` serait public dans le schéma exporté bien qu'il ait été défini comme privé dans le substitut. Grâce à l'utilisation de cette méthode, dans le schéma exporté, le modificateur d'accès peut être généré comme privé.  
  
### <a name="getreferencedtypeonimport-method"></a>Méthode GetReferencedTypeOnImport  

 Cette méthode mappe le <xref:System.Type> du substitut au type d'origine. Cette méthode est facultative pour l'importation de schéma.  
  
 Lors de la création d’un substitut qui importe un schéma et génère le code pour celui-ci, la tâche suivante consiste à définir le type d’une instance de substitution à son type d’origine.  
  
 Si le code généré doit faire référence à un type utilisateur existant, cette opération est effectuée en implémentant la méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A>.  
  
 Lors de l'importation d'un schéma, cette méthode est appelée pour chaque déclaration de type afin de mapper le contrat de données substitué à un type. Les paramètres chaîne `typeName` et `typeNamespace` définissent le nom et l'espace de noms du type substitué. La valeur de retour pour <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> est utilisée pour déterminer si un nouveau type doit être généré. Cette méthode doit retourner un type valide ou null. Pour les types valides, le type retourné sera utilisé en tant que type référencé dans le code généré. Si null est retourné, aucun type ne sera référencé et un nouveau type doit être créé. S'il existe plusieurs substituts, il est possible d'effectuer le mappage pour chaque type de substitution vers son type initial.  
  
 Le paramètre `customData` est l'objet initialement retourné à partir de <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. Ce `customData` est utilisé lorsque des auteurs de substitution souhaitent insérer des données/conseils supplémentaires dans les métadonnées pour une utilisation pendant l'importation afin de générer le code.  
  
### <a name="processimportedtype-method"></a>Méthode ProcessImportedType  

 La méthode <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> personnalise tout type créé à partir de l'importation de schéma. Cette méthode est facultative.  
  
 Lors de l'importation d'un schéma, cette méthode permet de personnaliser tout type importé et toute information de compilation. Par exemple :  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 Durant l'importation, cette méthode est appelée pour chaque type généré. Modifiez le <xref:System.CodeDom.CodeTypeDeclaration> spécifié ou modifiez le <xref:System.CodeDom.CodeCompileUnit>. Cela inclut la modification du nom, des membres, des attributs et de nombreuses autres propriétés du `CodeTypeDeclaration`. En traitant le `CodeCompileUnit`, il est possible de modifier les directives, espaces de noms, assemblys référencés et plusieurs autres aspects.  
  
 Le paramètre `CodeTypeDeclaration` contient la déclaration de type DOM de code. Le paramètre `CodeCompileUnit` autorise la modification pour le traitement du code.  Le retour de `null` entraîne le rejet de la déclaration de type. Inversement, lors du retour d'un `CodeTypeDeclaration`, les modifications sont conservées.  
  
 Si des données personnalisées sont insérées pendant l'exportation des métadonnées, elles doivent être fournies à l'utilisateur pendant l'importation afin de pouvoir être utilisées. Ces données personnalisées peuvent être utilisées pour des conseils de modèle de programmation ou autres commentaires. Chaque instance `CodeTypeDeclaration` et <xref:System.CodeDom.CodeTypeMember> inclut des données personnalisées en tant que propriété <xref:System.CodeDom.CodeObject.UserData%2A>, faisant l'objet d'un cast en type `IDataContractSurrogate`.  
  
 L'exemple ci-dessus apporte des modifications au schéma importé. Le code conserve des membres privés du type d'origine en utilisant un substitut. Le modificateur d’accès par défaut lors de l’importation d’un schéma est `public`. Par conséquent, tous les membres du schéma de substitution seront publics à moins d'être modifiés, comme dans cet exemple. Pendant l'exportation, des données personnalisées sont insérées dans les métadonnées à propos des membres privés. L’exemple consulte les données personnalisées, vérifie si le modificateur d’accès est privé, puis rend le membre approprié privé en définissant ses attributs. Sans cette personnalisation, le membre `numpens` serait défini comme public au lieu de privé.  
  
### <a name="getknowncustomdatatypes-method"></a>Méthode GetKnownCustomDataTypes  

 Cette méthode obtient des types de données personnalisés définis à partir du schéma. Elle est facultative pour l'importation de schéma.  
  
 La méthode est appelée au début de l'exportation et de l'importation de schéma. Elle retourne les types de données personnalisés utilisés dans le schéma exporté ou importé. Un <xref:System.Collections.ObjectModel.Collection%601> (le paramètre `customDataTypes`), qui est une collection de types, est passé à la méthode. La méthode doit ajouter des types connus supplémentaires à cette collection. Les types de données personnalisés connus sont nécessaires pour activer la sérialisation et la désérialisation des données personnalisées à l’aide du <xref:System.Runtime.Serialization.DataContractSerializer>. Pour plus d’informations, consultez [types connus de contrat de données](../feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Implémentation d'un substitut  

 Pour utiliser le substitut de contrat de données dans WCF, vous devez suivre quelques procédures spéciales.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Pour utiliser un substitut pour la sérialisation et la désérialisation  

 Utilisez le <xref:System.Runtime.Serialization.DataContractSerializer> pour effectuer la sérialisation et la désérialisation des données avec le substitut. Le <xref:System.Runtime.Serialization.DataContractSerializer> est créé par le <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Le substitut doit également être spécifié.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Pour implémenter la sérialisation et la désérialisation  
  
1. Créez une instance du <xref:System.ServiceModel.ServiceHost> pour votre service. Pour obtenir des instructions complètes, consultez [programmation WCF de base](../basic-wcf-programming.md).  
  
2. Pour chaque <xref:System.ServiceModel.Description.ServiceEndpoint> de l'hôte de service spécifié, recherchez son <xref:System.ServiceModel.Description.OperationDescription>.  
  
3. Parcourez les comportements d'opération pour déterminer si une instance du <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> est détectée.  
  
4. Si un <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> est détecté, affectez à sa propriété <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> une nouvelle instance du substitut. Si aucun <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> n'est détecté, créez une instance et affectez au membre <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> du nouveau comportement une nouvelle instance du substitut.  
  
5. Pour finir, ajoutez ce nouveau comportement aux comportements d'opérations actuels, comme illustré dans l'exemple suivant :  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Pour utiliser un substitut pour l'importation de métadonnées  

 Lors de l'importation de métadonnées telles que WSDL et XSD pour générer le code côté client, le substitut doit être ajouté au composant responsable de la génération du code à partir du schéma XSD, <xref:System.Runtime.Serialization.XsdDataContractImporter>. Pour cela, modifiez directement le <xref:System.ServiceModel.Description.WsdlImporter> utilisé pour importer les métadonnées.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Pour implémenter un substitut pour l'importation de métadonnées  
  
1. Importez les métadonnées à l'aide de la classe <xref:System.ServiceModel.Description.WsdlImporter>.  
  
2. Utilisez la méthode <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> pour vérifier si un <xref:System.Runtime.Serialization.XsdDataContractImporter> a été défini.  
  
3. Si la méthode <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> retourne la valeur `false`, créez un <xref:System.Runtime.Serialization.XsdDataContractImporter> et affectez à sa propriété <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> une nouvelle instance de la classe <xref:System.Runtime.Serialization.ImportOptions>. Autrement, utilisez l'importateur retourné par le paramètre `out` de la méthode <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>.  
  
4. Si le <xref:System.Runtime.Serialization.XsdDataContractImporter> n'a aucun <xref:System.Runtime.Serialization.ImportOptions> défini, affectez à la propriété une nouvelle instance de la classe <xref:System.Runtime.Serialization.ImportOptions>.  
  
5. Affectez à la propriété <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> du <xref:System.Runtime.Serialization.ImportOptions> du <xref:System.Runtime.Serialization.XsdDataContractImporter> une nouvelle instance du substitut.  
  
6. Ajoutez le <xref:System.Runtime.Serialization.XsdDataContractImporter> à la collection retournée par la propriété <xref:System.ServiceModel.Description.MetadataExporter.State%2A> du <xref:System.ServiceModel.Description.WsdlImporter> (héritée de la classe <xref:System.ServiceModel.Description.MetadataExporter>.)  
  
7. Utilisez la méthode <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> du <xref:System.ServiceModel.Description.WsdlImporter> pour importer tous les contrats de données dans le schéma. Durant la dernière étape, le code est généré à partir des schémas chargés en appelant le substitut.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Pour utiliser un substitut pour l'exportation de métadonnées  

 Par défaut, lors de l’exportation de métadonnées à partir de WCF pour un service, les schémas WSDL et XSD doivent être générés. Le substitut doit être ajouté au composant responsable de la génération du schéma XSD pour les types de contrat de données, <xref:System.Runtime.Serialization.XsdDataContractExporter>. Pour cela, utilisez un comportement qui implémente <xref:System.ServiceModel.Description.IWsdlExportExtension> pour modifier le <xref:System.ServiceModel.Description.WsdlExporter> ou modifiez directement le <xref:System.ServiceModel.Description.WsdlExporter> utilisé pour exporter les métadonnées.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Pour utiliser un substitut pour l'exportation de métadonnées  
  
1. Créez un <xref:System.ServiceModel.Description.WsdlExporter> ou utilisez le paramètre `wsdlExporter` passé à la méthode <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A>.  
  
2. Utilisez la fonction <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> pour vérifier si un <xref:System.Runtime.Serialization.XsdDataContractExporter> a été défini.  
  
3. Si <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> retourne la valeur `false`, créez un <xref:System.Runtime.Serialization.XsdDataContractExporter> avec les schémas XML générés à partir du <xref:System.ServiceModel.Description.WsdlExporter> et ajoutez-le à la collection retournée par la propriété <xref:System.ServiceModel.Description.MetadataExporter.State%2A> du <xref:System.ServiceModel.Description.WsdlExporter>. Autrement, utilisez l'exportateur retourné par le paramètre `out` de la méthode <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>.  
  
4. Si le <xref:System.Runtime.Serialization.XsdDataContractExporter> n'a aucun <xref:System.Runtime.Serialization.ExportOptions> défini, affectez à la propriété <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> une nouvelle instance de la classe <xref:System.Runtime.Serialization.ExportOptions>.  
  
5. Affectez à la propriété <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> du <xref:System.Runtime.Serialization.ExportOptions> du <xref:System.Runtime.Serialization.XsdDataContractExporter> une nouvelle instance du substitut. Les étapes suivantes d'exportation des métadonnées ne requièrent pas de modifications.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [Utilisation de contrats de données](../feature-details/using-data-contracts.md)
