---
title: Importation du schéma pour générer des classes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
ms.openlocfilehash: 01f5162727a213fa5dcdf8a70e4e8e4c3627f086
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596901"
---
# <a name="importing-schema-to-generate-classes"></a>Importation du schéma pour générer des classes
Pour générer des classes à partir de schémas utilisables avec Windows Communication Foundation (WCF), utilisez la <xref:System.Runtime.Serialization.XsdDataContractImporter> classe. Cette rubrique décrit le processus et les variations.  
  
## <a name="the-import-process"></a>Processus d'importation
 Le processus d'importation du schéma démarre avec un <xref:System.Xml.Schema.XmlSchemaSet> et produit un <xref:System.CodeDom.CodeCompileUnit>.  
  
 Le `XmlSchemaSet` fait partie du modèle d’objet de schéma (SOM) de .NET Framework qui représente un jeu de documents de schéma en langage XSD (XML Schema Definition). Pour créer un objet `XmlSchemaSet` à partir d'un jeu de documents XSD, désérialisez chaque document dans un objet <xref:System.Xml.Schema.XmlSchema> (à l'aide du <xref:System.Xml.Serialization.XmlSerializer>) et ajoutez ces objets à un nouveau `XmlSchemaSet`.  
  
 Le `CodeCompileUnit` fait partie du Code Document Object Model de l' .NET Framework (CodeDom) qui représente .NET Framework code de manière abstraite. Pour générer le code réel à partir d'un `CodeCompileUnit`, utilisez une sous-classe de la classe <xref:System.CodeDom.Compiler.CodeDomProvider>, telle que la classe <xref:Microsoft.CSharp.CSharpCodeProvider> ou <xref:Microsoft.VisualBasic.VBCodeProvider>.  
  
### <a name="to-import-a-schema"></a>Pour importer un schéma  
  
1. Créez une instance de <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2. facultatif. Passez un `CodeCompileUnit` dans le constructeur. Les types générés pendant l'importation de schéma sont ajoutés à cette instance `CodeCompileUnit` au lieu de démarrer avec un `CodeCompileUnit` vide.  
  
3. facultatif. Appelez une des méthodes <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> . La méthode détermine si le schéma donné est un schéma de contrat de données valide et peut être importé. La méthode `CanImport` a les mêmes surcharges que `Import` (étape suivante).  
  
4. Appelez l'une des méthodes `Import` surchargées, par exemple, la méthode <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29>.  
  
     La surcharge la plus simple prend un `XmlSchemaSet` et importe tous les types, y compris les types anonymes figurant dans ce jeu de schémas. D'autres surcharges vous permettent de spécifier le type XSD ou une liste de types à importer (sous la forme d'un <xref:System.Xml.XmlQualifiedName> ou d'une collection d'objets `XmlQualifiedName`). Dans ce cas, seuls les types spécifiés sont importés. Une surcharge prend un <xref:System.Xml.Schema.XmlSchemaElement> qui importe un élément particulier hors du `XmlSchemaSet`, ainsi que son type associé (qu'il soit anonyme ou non). Cette surcharge retourne un `XmlQualifiedName` qui représente le nom de contrat de données du type généré pour cet élément.  
  
     Plusieurs appels de la méthode `Import` entraînent l'ajout de plusieurs éléments au même `CodeCompileUnit`. Un type n'est pas généré dans le `CodeCompileUnit` s'il est déjà présent. Appelez plusieurs fois `Import` sur le même `XsdDataContractImporter` au lieu d'utiliser plusieurs objets `XsdDataContractImporter`. Il s'agit de la méthode recommandée pour éviter de générer des types en double.  
  
    > [!NOTE]
    > En cas de défaillance pendant l'importation, le `CodeCompileUnit` sera dans un état imprévisible. L'utilisation d'un `CodeCompileUnit` issu d'une importation ayant échoué pourrait vous exposer à des failles de sécurité.  
  
5. Accédez à `CodeCompileUnit` à l'aide de la propriété <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> .  
  
### <a name="import-options-customizing-the-generated-types"></a>Option d'importation : personnalisation des types générés  
 Vous pouvez définir la propriété <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> de <xref:System.Runtime.Serialization.XsdDataContractImporter> avec une instance de la classe <xref:System.Runtime.Serialization.ImportOptions> pour contrôler divers aspect du processus d'importation. Plusieurs options influencent directement les types générés.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Contrôle du niveau d'accès (GenerateInternal ou le commutateur /internal)  
 Cela correspond au commutateur **/Internal** sur l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Normalement, les types publics sont générés à partir d'un schéma, avec les champs privés et les propriétés de membres de données publiques correspondantes. Pour générer des types internes à la place, affectez à la propriété <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> la valeur `true`.  
  
 L'exemple suivant affiche un schéma transformé en une classe interne lorsque la propriété <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> a la valeur `true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Contrôle des espaces de noms (espaces de noms ou le commutateur /namespace)  
 Cela correspond au commutateur **/namespace** sur l' `Svcutil.exe` outil.  
  
 Normalement, les types générés à partir du schéma sont générés dans des espaces de noms .NET Framework, chaque espace de noms XSD correspondant à un espace de noms .NET Framework spécifique selon un mappage décrit dans [référence de schéma de contrat de données](data-contract-schema-reference.md). Vous pouvez personnaliser ce mappage par la propriété <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> à un <xref:System.Collections.Generic.Dictionary%602>. Si un espace de noms XSD donné est trouvé dans le dictionnaire, l’espace de noms .NET Framework correspondant est également extrait de votre dictionnaire.  
  
 Par exemple, considérons le schéma suivant.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 L’exemple suivant utilise la `Namespaces` propriété pour mapper l' `http://schemas.contoso.com/carSchema` espace de noms à « contoso. Cars ».  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Ajout de SerializableAttribute (GenerateSerializable ou le commutateur /serializable)  
 Cela correspond au commutateur **/Serializable** sur l' `Svcutil.exe` outil.  
  
 Parfois, il est important que les types générés à partir du schéma soient utilisables avec .NET Framework moteurs de sérialisation du Runtime (par exemple, les <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes et). Cela est utile lors de l’utilisation de types pour la communication à distance .NET Framework. Pour ce faire, vous devez appliquer l'attribut <xref:System.SerializableAttribute> aux types générés en plus de l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> standard. L'attribut est généré automatiquement si l'option d'importation `GenerateSerializable` a la valeur `true`.  
  
 L'exemple suivant affiche la classe `Vehicle` générée lorsque l'option d'importation `GenerateSerializable` a la valeur `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Ajout de la prise en charge de la liaisons de données (EnableDataBinding ou le commutateur /enableDataBinding)  
 Cela correspond au commutateur **/enableDataBinding** sur l’outil Svcutil. exe.  
  
 Il est parfois utile de lier les types générés à partir du schéma à des composants d'interface utilisateur graphique afin que toute mise à jour des instances de ces types mette à jour automatiquement l'interface utilisateur. `XsdDataContractImporter` peut générer des types qui implémentent l'interface <xref:System.ComponentModel.INotifyPropertyChanged> afin que toute modification de propriété déclenche un événement. Si vous générez des types à utiliser avec un environnement de programmation d’interface utilisateur client qui prend en charge cette interface (par exemple, Windows Presentation Foundation WPF), affectez à la propriété la valeur <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> `true` pour activer cette fonctionnalité.  
  
 L'exemple suivant affiche la classe `Vehicle` générée lorsque <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> a la valeur `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Options d’importation : choix des types de collection  
 Deux modèles spéciaux au format XML représentent des collections d’éléments : les listes d’éléments et les associations entre un élément et un autre. Les éléments suivants sont un exemple d'une liste de chaînes.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Les éléments suivants sont un exemple d'une association entre une chaîne et un entier (`city name` et `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
> Toute association peut aussi être considérée comme une liste. Par exemple, vous pouvez considérer l'association précédente comme une liste d'objets `city` complexes qui contiennent deux champs (un champ de chaîne et un champ d'entier). Les deux modèles sont représentés dans le schéma XSD. Il n’existe aucun moyen de faire la différence entre une liste et une association. de ce fait, ces modèles sont toujours traités comme des listes, sauf si une annotation spéciale spécifique à WCF est présente dans le schéma. L’annotation indique qu’un modèle donné représente une association. Pour plus d’informations, consultez [Référence du schéma de contrat de données](data-contract-schema-reference.md).  
  
 Normalement, une liste est importée sous la forme d’un contrat de données de collection qui dérive d’une liste générique ou d’un tableau de .NET Framework, selon que le schéma respecte ou non le modèle d’affectation de noms standard pour les collections. Cela est décrit plus en détail dans les [types de collections dans les contrats de données](collection-types-in-data-contracts.md). Les associations sont importées normalement comme <xref:System.Collections.Generic.Dictionary%602> ou comme un contrat de données de collection qui dérive de l'objet dictionnaire. Par exemple, considérons le schéma suivant.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 Celui-ci serait importé comme suit (les champs sont montrés au lieu des propriétés à des fin de lisibilité).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Il est possible de personnaliser les types de collection générés pour ces modèles de schéma. Par exemple, vous pouvez générer des collections qui dérivent de <xref:System.ComponentModel.BindingList%601> au lieu de la classe <xref:System.Collections.Generic.List%601> afin de lier le type à une zone de liste et qu'il soit mis à jour automatiquement si le contenu de la collection est modifié. Pour cela, affectez à la propriété <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> de la classe <xref:System.Runtime.Serialization.ImportOptions> une liste de types de collection à utiliser (définis ci-dessous comme les types référencés). Lors de l’importation d’une collection, cette liste de types de collection référencés est analysée et la collection qui correspond le mieux est utilisée, s’il en existe une. Les associations sont mappées uniquement aux types qui implémentent l'interface générique ou non générique <xref:System.Collections.IDictionary>, tandis que les listes sont mappées à tout type de collection pris en charge.  
  
 Par exemple, si la propriété <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> a la valeur d'un <xref:System.ComponentModel.BindingList%601>, le type `people` dans l'exemple précédent est généré comme suit.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Un type générique fermé est considéré comme la meilleure correspondance. Par exemple, si les types `BindingList(Of Integer)` et <xref:System.Collections.ArrayList> sont passés à la collection de types référencés, toutes les listes d'entiers présentes dans le schéma sont importées comme `BindingList(Of Integer)`. Toutes les autres listes, par exemple `List(Of String)`, sont importées comme `ArrayList`.  
  
 Si un type qui implémente l'interface `IDictionary` générique est ajouté à la collection de types référencés, ses paramètres de type doivent être complètement ouverts ou complètement fermés.  
  
 Les doublons ne sont pas autorisés. Par exemple, vous ne pouvez pas ajouter à la fois `List(Of Integer)` et `Collection(Of Integer)` aux types référencés. Il serait alors impossible de déterminer lequel doit être utilisé lorsqu'une liste d'entiers est présente dans le schéma. Les doublons sont détectés uniquement si un type présent dans le schéma expose le problème des doublons. Par exemple, si le schéma importé ne contient pas de listes d’entiers, il est possible que la collection de types référencés contiennent à la fois `List(Of Integer)` et `Collection(Of Integer)`, mais aucun n’aura d’effet.  
  
 Le mécanisme des types de collection référencés fonctionne également bien pour les collections de types complexes (y compris les collections d’autres collections), et pas seulement pour les collections de primitives.  
  
 La `ReferencedCollectionTypes` propriété correspond au commutateur **/CollectionType** sur l’outil Svcutil. exe. Notez que pour référencer plusieurs types de collection, le commutateur **/CollectionType** doit être spécifié plusieurs fois. Si le type n’est pas dans le fichier MsCorLib. dll, son assembly doit également être référencé à l’aide du commutateur **/Reference** .  
  
#### <a name="import-options-referencing-existing-types"></a>Options d'importation : référencement de types existants  
 Parfois, les types dans le schéma correspondent à des types de .NET Framework existants, et il n’est pas nécessaire de générer ces types à partir de zéro. (Cette section s'applique uniquement aux types qui ne sont pas des collections. Pour les types de collection, consultez la section précédente.)  
  
 Par exemple, vous avez peut-être un type standard de contrat de données « Person » dans l'entreprise que vous souhaitez toujours utiliser pour représenter une personne. Chaque fois que certains services font appel à ce type, et que son schéma apparaît dans les métadonnées de service, vous pouvez réutiliser le type `Person` existant lorsque vous importez ce schéma au lieu d'en générer un nouveau pour chaque service.  
  
 Pour ce faire, transmettez une liste de types de .NET Framework que vous souhaitez réutiliser dans la collection que la <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> propriété retourne sur la <xref:System.Runtime.Serialization.ImportOptions> classe. Si chacun de ces types a un nom et un espace de noms de contrat de données qui correspondent au nom et à l'espace de noms d'un type de schéma, une comparaison structurelle est effectuée. S’il est déterminé que les types ont à la fois des noms correspondants et des structures correspondantes, le type de .NET Framework existant est réutilisé au lieu d’en générer un nouveau. Si seul le nom correspond mais pas la structure, une exception est levée. Notez qu'il n'y a aucune ressource pour le suivi des versions lors du référencement des types (par exemple, si vous ajoutez des membres de données facultatifs). Les structures doivent correspondre exactement.  
  
 Il est permis d’ajouter plusieurs types avec le même nom et espace de noms de contrat de données à la collection de types référencée, tant qu’aucun type de schéma n’est importé avec ce nom et cet espace de noms. Vous pouvez ainsi ajouter facilement tous les types dans un assembly à la collection sans tenir compte des doublons pour les types qui n’apparaissent pas réellement dans le schéma.  
  
 La `ReferencedTypes` propriété correspond au commutateur **/Reference** dans certains modes de fonctionnement de l’outil Svcutil. exe.  
  
> [!NOTE]
> Quand vous utilisez Svcutil. exe ou (dans Visual Studio) les outils **Ajouter une référence de service** , tous les types dans mscorlib. dll sont référencés automatiquement.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Options d'importation : importer le schéma non DataContract comme types IXmlSerializable  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> prend en charge un sous-ensemble limité du schéma. Si des constructions de schéma non prises en charge sont présentes (par exemple, les attributs XML), la tentative d'importation échoue et génère une exception. Cependant, affecter à la propriété <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> la valeur `true` étend la plage de schéma prise en charge. Une fois qu'elle a la valeur `true`, la propriété <xref:System.Runtime.Serialization.XsdDataContractImporter> génère des types qui implémentent l'interface <xref:System.Xml.Serialization.IXmlSerializable>. Cette opération permet d'accéder directement à la représentation XML de ces types.  
  
##### <a name="design-considerations"></a>Remarques sur la conception  
  
- Il peut s'avérer difficile d'utiliser directement la représentation XML faiblement typée. Vous pouvez faire appel à un moteur de sérialisation différent, tel que <xref:System.Xml.Serialization.XmlSerializer>, pour utiliser d'une manière fortement typée un schéma incompatible avec les contrats de données. Pour plus d’informations, consultez [utilisation de la classe XmlSerializer](using-the-xmlserializer-class.md).  
  
- Certaines constructions de schéma ne peuvent pas être importées par <xref:System.Runtime.Serialization.XsdDataContractImporter> même lorsque la propriété <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> a la valeur `true`. Là encore, utilisez <xref:System.Xml.Serialization.XmlSerializer> pour ces cas.  
  
- Les constructions de schéma exactes qui sont prises en charge lorsque <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> est `true` ou `false` sont décrites dans [référence de schéma de contrat de données](data-contract-schema-reference.md).  
  
- Le schéma pour les types <xref:System.Xml.Serialization.IXmlSerializable> générés ne conservent pas le respect lors de l'importation ou de l'exportation. Autrement dit, l'exportation du schéma à partir des types générés et son importation sous la forme de classes ne retournent pas le schéma d'origine.  
  
 Il est possible d'associer l'option <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> à l'option <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> décrite précédemment. Pour les types qui doivent être générés comme des implémentations <xref:System.Xml.Serialization.IXmlSerializable>, le contrôle structurel est ignoré lors de l'utilisation de la fonctionnalité <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A>.  
  
 L' <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> option correspond au commutateur **/importXmlTypes** sur l’outil Svcutil. exe.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Utilisation des types IXmlSerializable générés  
 Les types `IXmlSerializable` générés contiennent un champ privé, nommé « nodesField », qui retourne un tableau d'objets <xref:System.Xml.XmlNode>. Lorsque vous désérialisez une instance de ce type, vous pouvez accéder directement aux données XML par l'intermédiaire de ce champ en utilisant le modèle objet de document XML. Lorsque vous sérialisez une instance de ce type, vous pouvez affecter à ce champ les données XML souhaitées pour qu'il soit sérialisé.  
  
 Cette opération est possible grâce à l'implémentation `IXmlSerializable`. Dans le type `IXmlSerializable` généré, l'implémentation <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> appelle la méthode <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> de la classe <xref:System.Runtime.Serialization.XmlSerializableServices>. La méthode est une méthode d'assistance qui convertit le code XML fournie par <xref:System.Xml.XmlReader> sous la forme d'un tableau d'objets <xref:System.Xml.XmlNode>. L'implémentation <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> effectue l'opération inverse et convertit le tableau d'objets `XmlNode` sous la forme d'une séquence d'appels <xref:System.Xml.XmlWriter>. Cette opération est possible grâce à la méthode <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A>.  
  
 Il est possible d'exécuter le processus d'exportation de schéma sur les classes `IXmlSerializable` générées. Comme indiqué précédemment, le schéma d'origine n'est pas récupéré. Au lieu de cela, vous obtiendrez le type XSD standard « anyType », qui est un caractère générique pour tout type XSD.  
  
 Pour ce faire, <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> vous devez appliquer l’attribut aux `IXmlSerializable` classes générées et spécifier une méthode qui appelle la <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> méthode afin de générer le type « anyType ».  
  
> [!NOTE]
> Le type <xref:System.Runtime.Serialization.XmlSerializableServices> est destiné uniquement à la prise en charge de cette fonctionnalité particulière. Il n'est pas recommandé de l'utiliser à d'autres fins.  
  
#### <a name="import-options-advanced-options"></a>Options d'importation : options avancées  
 Les éléments suivants représentent les options d'importation avancées :  
  
- Propriété <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>. Spécifiez la <xref:System.CodeDom.Compiler.CodeDomProvider> à utiliser pour générer le code destiné aux classes générées. Le mécanisme d’importation cherche à éviter les fonctionnalités que la <xref:System.CodeDom.Compiler.CodeDomProvider> ne prend pas en charge. Si le <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> n’est pas défini, l’ensemble complet des fonctionnalités de .NET Framework est utilisé sans aucune restriction.  
  
- Propriété <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>. Une implémentation <xref:System.Runtime.Serialization.IDataContractSurrogate> peut être spécifiée avec cette propriété. <xref:System.Runtime.Serialization.IDataContractSurrogate> personnalise le processus d'importation. Pour plus d’informations, consultez [substituts de contrat de données](../extending/data-contract-surrogates.md). Par défaut, aucun substitut n'est utilisé.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- <xref:System.Runtime.Serialization.ImportOptions>
- [Référence des schémas de contrats de données](data-contract-schema-reference.md)
- [Substituts de contrats de données](../extending/data-contract-surrogates.md)
- [Importation et exportation de schémas](schema-import-and-export.md)
- [Exportation de schémas à partir de classes](exporting-schemas-from-classes.md)
- [Référence des schémas de contrats de données](data-contract-schema-reference.md)
