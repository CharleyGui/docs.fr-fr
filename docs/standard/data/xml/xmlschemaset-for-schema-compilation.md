---
title: XmlSchemaSet pour la compilation de schémas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 4501f3dde8d402bd318332dfe9b2209b3febea71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723361"
---
# <a name="xmlschemaset-for-schema-compilation"></a>XmlSchemaSet pour la compilation de schémas

Décrit l'objet <xref:System.Xml.Schema.XmlSchemaSet>, un cache où les schémas de langage XSD (XML Schema Definition) peuvent être stockés et validés.  
  
## <a name="the-xmlschemaset-class"></a>Classe XmlSchemaSet  

 L'objet <xref:System.Xml.Schema.XmlSchemaSet> est un cache où les schémas de langage XSD (XML Schema Definition) peuvent être stockés et validés.  
  
 Dans <xref:System.Xml?displayProperty=nameWithType> version 1.0, les schémas XML ont été chargés dans une classe <xref:System.Xml.Schema.XmlSchemaCollection> sous la forme d'une bibliothèque de schémas. Dans <xref:System.Xml?displayProperty=nameWithType> version 2.0, les classes <xref:System.Xml.XmlValidatingReader> et <xref:System.Xml.Schema.XmlSchemaCollection> sont obsolètes et ont été respectivement remplacées par les méthodes <xref:System.Xml.XmlReader.Create%2A> et la classe <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> a été introduit pour résoudre un certain nombre de problèmes, notamment la compatibilité aux normes, les performances et le format de schéma XDR (XML-Data Reduced) obsolète de Microsoft.  
  
 Voici une comparaison entre la classe <xref:System.Xml.Schema.XmlSchemaCollection> et la classe <xref:System.Xml.Schema.XmlSchemaSet>.  
  
|XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Prend en charge les schémas XML du W3C et XDR de Microsoft.|Ne prend en charge que les schémas XML du W3C.|  
|Les schémas sont compilés lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A>.|Les schémas ne sont pas compilés lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>. Les performances sont ainsi améliorées lors de la création de la bibliothèque de schémas.|  
|Chaque schéma génère une version compilée individuelle pouvant se traduire par des « îlots de schémas ». Par conséquent, toutes les inclusions et importations se trouvent dans la portée de ce schéma uniquement.|Les schémas compilés génèrent un seul schéma logique, un « ensemble » de schémas. Tous les schémas importés dans un schéma qui est ajouté à l'ensemble sont également directement ajoutés à l'ensemble. Tous les types sont donc disponibles pour tous les schémas.|  
|Un seul schéma peut exister dans la collection pour un espace de noms cible particulier.|Plusieurs schémas peuvent être ajoutés pour le même espace de noms cible tant qu'aucun conflit de type ne survient.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migration vers XmlSchemaSet  

 L'exemple de code suivant fournit un guide pour la migration vers la nouvelle classe <xref:System.Xml.Schema.XmlSchemaSet> à partir de la classe <xref:System.Xml.Schema.XmlSchemaCollection> obsolète. L'exemple de code illustre les principales différences suivantes entre les deux classes.  
  
- Contrairement à la méthode <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> de la classe <xref:System.Xml.Schema.XmlSchemaCollection>, les schémas ne sont pas compilés lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>. La méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> est explicitement appelée dans l'exemple de code.  
  
- Pour itérer sur un objet <xref:System.Xml.Schema.XmlSchemaSet>, vous devez utiliser la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Voici un exemple de code <xref:System.Xml.Schema.XmlSchemaCollection> obsolète.  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 Voici un exemple de code <xref:System.Xml.Schema.XmlSchemaSet> équivalent.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a>Ajout et récupération de schémas  

 Les schémas sont ajoutés à un objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>. Lorsqu'un schéma est ajouté à un objet <xref:System.Xml.Schema.XmlSchemaSet>, il est associé à un URI d'espace de noms cible. L'URI d'espace de noms cible peut être spécifié sous la forme d'un paramètre pour la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> ou si aucun espace de noms cible n'est spécifié, l'objet <xref:System.Xml.Schema.XmlSchemaSet> utilise l'espace de noms cible défini dans le schéma.  
  
 Les schémas sont récupérés à partir d'un objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide de la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>. La propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> permet d'itérer sur les objets <xref:System.Xml.Schema.XmlSchema> contenus dans l'objet <xref:System.Xml.Schema.XmlSchemaSet>. La propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> retourne tous les objets <xref:System.Xml.Schema.XmlSchema> contenus dans l'objet <xref:System.Xml.Schema.XmlSchemaSet> ou, en cas de fourniture d'un paramètre d'espace de noms cible, tous les objets <xref:System.Xml.Schema.XmlSchema> qui appartiennent à l'espace de noms cible. Si `null` est spécifié comme paramètre d'espace de noms cible, la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> retourne tous les schémas sans espace de noms.  
  
 L'exemple suivant ajoute le schéma `books.xsd` de l'espace de noms `http://www.contoso.com/books` à un objet <xref:System.Xml.Schema.XmlSchemaSet>, récupère tous les schémas qui appartiennent à l'espace de noms `http://www.contoso.com/books` à partir de l'objet <xref:System.Xml.Schema.XmlSchemaSet>, puis écrit ces schémas dans l'objet <xref:System.Console>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 Pour plus d'informations sur l'ajout et la récupération de schémas à partir d'un objet <xref:System.Xml.Schema.XmlSchemaSet>, voir la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> et la documentation de référence sur la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.  
  
## <a name="compiling-schemas"></a>Compilation de schémas  

 Les schémas d'un objet <xref:System.Xml.Schema.XmlSchemaSet> sont compilés en un seul schéma logique par la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
> Contrairement à la classe <xref:System.Xml.Schema.XmlSchemaCollection> obsolète, les schémas ne sont pas compilés lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.  
  
 Si la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> s'exécute correctement, la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> est définie sur `true`.  
  
> [!NOTE]
> La propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> n'est pas affectée si les schémas sont modifiés dans l'objet <xref:System.Xml.Schema.XmlSchemaSet>. Le suivi des mises à jour des schémas individuels dans l'objet <xref:System.Xml.Schema.XmlSchemaSet> n'est pas assuré. Par conséquent, la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> peut être `true`, même si l'un des schémas contenus dans l'objet <xref:System.Xml.Schema.XmlSchemaSet> a été modifié, pour autant qu'aucun schéma n'a été ajouté ou supprimé de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 L'exemple suivant ajoute le fichier `books.xsd` à l'objet <xref:System.Xml.Schema.XmlSchemaSet>, puis appelle la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 Pour plus d'informations sur la compilation de schémas dans un objet <xref:System.Xml.Schema.XmlSchemaSet>, voir la documentation de référence sur la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.  
  
## <a name="reprocessing-schemas"></a>Nouveau traitement des schémas  

 Un nouveau traitement d'un schéma dans un objet <xref:System.Xml.Schema.XmlSchemaSet> effectue toutes les étapes de prétraitement sur un schéma lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>. Si l'appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> réussit, la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> est définie sur `false`.  
  
 La méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> doit être utilisée lorsqu'un schéma de l'objet <xref:System.Xml.Schema.XmlSchemaSet> a été modifié après l'exécution de la compilation par l'objet <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 L'exemple suivant illustre le nouveau traitement d'un schéma ajouté à l'objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>. Après la compilation de l'objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> et la modification du schéma ajouté à l'objet <xref:System.Xml.Schema.XmlSchemaSet>, la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> est définie sur `true`, même si un schéma de l'objet <xref:System.Xml.Schema.XmlSchemaSet> a été modifié. L'appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> exécute l'ensemble du prétraitement effectué par la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> et définit la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> sur `false`.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 Pour plus d'informations sur un nouveau traitement de schémas dans un objet <xref:System.Xml.Schema.XmlSchemaSet>, voir la documentation de référence sur la méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.  
  
## <a name="checking-for-a-schema"></a>Recherche d'un schéma  

 La méthode <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> peut permettre de vérifier la présence d'un schéma dans un objet <xref:System.Xml.Schema.XmlSchemaSet>. La méthode <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> prend un espace de noms cible ou un objet <xref:System.Xml.Schema.XmlSchema> à rechercher. Dans les deux cas, la méthode <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> retourne `true` si le schéma est contenu dans l'objet <xref:System.Xml.Schema.XmlSchemaSet> ; sinon, elle retourne `false`.  
  
 Pour plus d'informations sur la recherche d'un schéma, voir la documentation de référence sur la méthode <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>.  
  
## <a name="removing-schemas"></a>Suppression de schémas  

 Les schémas sont supprimés d'un objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide des méthodes <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> et <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>. La méthode <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> supprime le schéma spécifié de l'objet <xref:System.Xml.Schema.XmlSchemaSet>, tandis que la méthode <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> supprime le schéma spécifié et tous les schémas importés à partir de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 L'exemple suivant illustre l'ajout de plusieurs schémas à un objet <xref:System.Xml.Schema.XmlSchemaSet>, puis l'utilisation de la méthode <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> pour supprimer l'un des schémas et tous les schémas importés.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 Pour plus d'informations sur la suppression de schémas d'un objet <xref:System.Xml.Schema.XmlSchemaSet>, voir la documentation de référence sur les méthodes <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> et <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>.  
  
## <a name="schema-resolution-and-xsimport"></a>Résolution de schémas et xs:import  

 Les exemples suivants décrivent le comportement <xref:System.Xml.Schema.XmlSchemaSet> pour l'importation de schémas lorsque plusieurs schémas existent dans un objet <xref:System.Xml.Schema.XmlSchemaSet> pour un espace de noms donné.  
  
 Supposez par exemple qu'un objet <xref:System.Xml.Schema.XmlSchemaSet> contienne plusieurs schémas pour l'espace de noms `http://www.contoso.com`. Un schéma présentant la directive `xs:import` est ajouté à l'objet <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 L'objet <xref:System.Xml.Schema.XmlSchemaSet> tente d'importer un schéma pour l'espace de noms `http://www.contoso.com` en le chargeant à partir de l'URL `http://www.contoso.com/schema.xsd`. Seuls la déclaration de schéma et les types déclarés dans le document de schéma sont disponibles dans le schéma d'importation, même si d'autres documents de schéma existent pour l'espace de noms `http://www.contoso.com` dans l'objet <xref:System.Xml.Schema.XmlSchemaSet>. Si le fichier `schema.xsd` est introuvable à l'URL `http://www.contoso.com/schema.xsd`, aucun schéma n'est importé dans le schéma d'importation pour l'espace de noms `http://www.contoso.com`.  
  
## <a name="validating-xml-documents"></a>Validation de documents XML  

 Les document XML peuvent être validés par rapport à des schémas dans un objet <xref:System.Xml.Schema.XmlSchemaSet>. Pour valider un document XML, ajoutez un schéma à la propriété <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> d'un objet <xref:System.Xml.XmlReaderSettings>, ou ajoutez un objet <xref:System.Xml.Schema.XmlSchemaSet> à la propriété <xref:System.Xml.XmlReaderSettings.Schemas%2A> d'un objet <xref:System.Xml.XmlReaderSettings>. L'objet <xref:System.Xml.XmlReaderSettings> est ensuite utilisé par la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader> pour créer un objet <xref:System.Xml.XmlReader> et valider le document XML.  
  
 Pour plus d’informations sur la validation de documents XML à l’aide d’un <xref:System.Xml.Schema.XmlSchemaSet>, consultez [Validation de schéma XML (XSD) avec XmlSchemaSet](xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [XmlSchemaSet en tant que cache de schéma](xmlschemaset-for-schema-compilation.md)
- [Validation de schéma XML (XSD) avec XmlSchemaSet](xml-schema-xsd-validation-with-xmlschemaset.md)
