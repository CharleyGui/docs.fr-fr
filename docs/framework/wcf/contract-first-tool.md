---
title: Outil « Contrat en premier »
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 7ddc3b2c733c73808d17b6e0f45129cc19d7527c
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380375"
---
# <a name="contract-first-tool"></a>Outil « Contrat en premier »
Les contrats de service doivent souvent être créés à partir de services existants. Dans .NET Framework 4.5, les classes de contrat de données peuvent être créés automatiquement à partir des services existants à l’aide de l’outil contrat en premier. Pour utiliser l'outil Contrat en premier, le fichier de définition de schéma XML (XSD) doit être téléchargé localement ; l'outil ne peut pas importer les contrats de données distants via HTTP.

 L’outil contrat en premier est intégré dans Visual Studio 2012 comme une tâche de génération. Les fichiers de code générés par la tâche de génération sont créés à chaque fois que le projet est généré, afin que le projet puisse facilement adopter les modifications du contrat de service sous-jacent.

 Les types de schémas que l'outil Contrat en premier peut importer sont les suivants :

```xml
<xsd:complexType>
<xsd:simpleType>
```

 Les types simples ne seront pas générés s'ils sont des primitives telles que `Int16` ou `String` ; les types complexes ne seront pas générés s'ils sont de type `Collection`. Les types ne seront pas non plus générés s'ils font partie d'un autre `xsd:complexType`. Dans tous ces cas, les types seront référencés dans les types existants du projet à la place.

## <a name="adding-a-data-contract-to-a-project"></a>Ajout d'un contrat de données à un projet
 Pour utiliser l'outil Contrat en premier, le contrat de service (XSD) doit être ajouté au projet. Pour les besoins de cette présentation, le contrat suivant sera utilisé pour illustrer les fonctions Contrat en premier. Cette définition de service est un sous-ensemble du contrat de service utilisé par l'API de recherche Bing.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema id="ServiceSchema"
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"
    elementFormDefault="qualified"
    xmlns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
>
  <xs:complexType name="SearchRequest">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="WebSearchOption">
    <xs:restriction base="xs:string">
      <xs:enumeration value="DisableHostCollapsing" />
      <xs:enumeration value="DisableQueryAlterations" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

 Pour ajouter le contrat de service ci-dessus au projet, cliquez sur le projet et sélectionnez **Ajouter nouveau...** . Sélectionnez la définition de schéma dans le volet WCF de la boîte de dialogue Modèles et nommez le nouveau fichier SampleContract.xsd. Copiez et collez le code ci-dessus dans le mode Code du nouveau fichier.

## <a name="configuring-contract-first-options"></a>Configuration des options Contrat en premier
 Options de contrat en premier peuvent être configurées dans le menu des propriétés d’un projet WCF. Pour activer le développement contrat en premier, sélectionnez le **activer le XSD comme langage de définition de Type** case à cocher dans la page WCF de la fenêtre de propriétés de projet.

 ![Capture d’écran des Options WCF avec développement contrat en premier est activée.](./media/contract-first-tool/contract-first-options.png)

 Pour configurer les propriétés avancées, cliquez sur le bouton Avancées.

 ![Boîte de dialogue Paramètres de génération de Code de contrat avancée.](./media/contract-first-tool/advanced-contract-settings.png)

 Les paramètres avancés suivants peuvent être configurés pour la génération du code à partir des contrats. Les paramètres peuvent être configurés pour tous les fichiers du projet ; les paramètres ne peuvent pas être configurés pour les fichiers individuels à ce stade.

- **Mode de sérialiseur**: Ce paramètre détermine le sérialiseur utilisé pour la lecture des fichiers de contrat de service. Lorsque **sérialiseur XML** est sélectionnée, le **Types de collections** et **réutiliser les Types** options sont désactivées. Ces options s’appliquent uniquement à la **Data Contract Serializer**.

- **Réutiliser les Types**: Ce paramètre spécifie les bibliothèques qui sont utilisées pour la réutilisation du type. Ce paramètre s’applique uniquement si **Mode de sérialiseur** a la valeur **Data Contract Serializer**.

- **Type de collection**: Ce paramètre spécifie le type qualifié complet ou qualifié d’assembly à utiliser pour le type de données de collection. Ce paramètre s’applique uniquement si **Mode de sérialiseur** a la valeur **Data Contract Serializer**.

- **Type de dictionnaire**: Ce paramètre spécifie le type qualifié complet ou qualifié d’assembly à utiliser pour le type de données de dictionnaire.

- **EnableDataBinding**: Ce paramètre spécifie s’il faut implémenter la <xref:System.ComponentModel.INotifyPropertyChanged> interface sur tous les types de données pour implémenter la liaison de données.

- **ExcludedTypes**: ce paramètre spécifie la liste des types complet ou qualifié d’assembly à exclure les assemblys référencés. Ce paramètre s’applique uniquement si **Mode de sérialiseur** a la valeur **Data Contract Serializer**.

- **GenerateInternalTypes**: Ce paramètre spécifie s’il faut générer des classes marquées comme internes. Ce paramètre s’applique uniquement si **Mode de sérialiseur** a la valeur **Data Contract Serializer**.

- **GenerateSerializableTypes**: Ce paramètre spécifie s’il faut générer des classes avec le <xref:System.SerializableAttribute> attribut. Ce paramètre s’applique uniquement si **Mode de sérialiseur** a la valeur **Data Contract Serializer**.

- **/Importxmltypes**: Ce paramètre spécifie s’il faut configurer le sérialiseur de contrat de données pour appliquer le <xref:System.SerializableAttribute> attribut aux classes sans le <xref:System.Runtime.Serialization.DataContractAttribute> attribut.  Ce paramètre s’applique uniquement si **Mode de sérialiseur** a la valeur **Data Contract Serializer**.

- **SupportFx35TypedDataSets**: Ce paramètre spécifie s’il faut fournir des fonctionnalités supplémentaires pour les jeux de données typés créés pour .NET Framework 3.5. Lorsque **Mode de sérialiseur** a la valeur **sérialiseur XML**, le <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> extension sera ajoutée à l’importateur de schéma XML lorsque cette valeur est définie sur True. Lorsque **Mode de sérialiseur** a la valeur **sérialiseur de contrat de données**, le type <xref:System.DateTimeOffset> sera exclu des références lorsque cette valeur est définie sur False, afin qu’un <xref:System.DateTimeOffset> est toujours généré pour les versions antérieures du framework.

- **InputXsdFiles**: Ce paramètre spécifie la liste des fichiers d’entrée. Chaque fichier doit contenir un schéma XML valide.

- **Langage**: Ce paramètre spécifie le langage du code généré de contrat. Le paramètre doit être reconnaissable par <xref:System.CodeDom.Compiler.CodeDomProvider>.

- **NamespaceMappings**: Ce paramètre spécifie les mappages des espaces de noms cibles XSD aux espaces de noms CLR. Chaque mappage doit utiliser le format suivant :

    ```xml
    "<Schema Namespace>, <CLR Namespace>"
    ```

     Le sérialiseur XML n'accepte qu'un seul mappage au format suivant :

    ```xml
    "*, <CLR Namespace>"
    ```

- **OutputDirectory**: Ce paramètre spécifie le répertoire où les fichiers de code sont générés.

 Les paramètres seront utilisés pour générer des types de contrat de service à partir des fichiers de contrat de service lorsque le projet est généré.

## <a name="using-contract-first-development"></a>Utilisation du développement Contrat en premier
 Après l’ajout du contrat de service au projet et en vérifiant les paramètres de génération, générez le projet en appuyant sur **F6**. Les types définis dans le contrat de service sont ensuite disponibles dans le projet.

 Pour utiliser les types définis dans le contrat de service, ajoutez une référence à `ContractTypes` sous l'espace de noms actuel :

```csharp
using MyProjectNamespace.ContractTypes;
```

 Les types définis dans le contrat de service peuvent ensuite être résolus dans le projet, comme indiqué ci-dessous :

 ![Classe de SearchRequest montrant dans IntelliSense, après avoir tapé les premières lettres.](./media/contract-first-tool/service-contract-types.png)

 Les types générés par l'outil sont créés dans le fichier GeneratedXSDTypes.cs. Le fichier est créé dans le \<répertoire du projet > /obj/\<configuration de build > répertoire /XSDGeneratedCode/ par défaut. L'exemple de schéma au début de cette rubrique est converti comme suit :

```csharp
//------------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by a tool.
//     Runtime Version:4.0.30319.17330
//
//     Changes to this file may cause incorrect behavior and will be lost if
//     the code is regenerated.
// </auto-generated>
//------------------------------------------------------------------------------

namespace TestXSD3.ContractTypes
{
    using System.Xml.Serialization;

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Diagnostics.DebuggerStepThroughAttribute()]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]
    public partial class SearchRequest
    {

        private string versionField;

        private string marketField;

        private string uILanguageField;

        private string queryField;

        private string appIdField;

        private double latitudeField;

        private bool latitudeFieldSpecified;

        private double longitudeField;

        private bool longitudeFieldSpecified;

        private double radiusField;

        private bool radiusFieldSpecified;

        public SearchRequest()
        {
            this.versionField = "2.2";
        }

        /// <remarks/>
        [System.ComponentModel.DefaultValueAttribute("2.2")]
        public string Version
        {
            get
            {
                return this.versionField;
            }
            set
            {
                this.versionField = value;
            }
        }

        /// <remarks/>
        public string Market
        {
            get
            {
                return this.marketField;
            }
            set
            {
                this.marketField = value;
            }
        }

        /// <remarks/>
        public string UILanguage
        {
            get
            {
                return this.uILanguageField;
            }
            set
            {
                this.uILanguageField = value;
            }
        }

        /// <remarks/>
        public string Query
        {
            get
            {
                return this.queryField;
            }
            set
            {
                this.queryField = value;
            }
        }

        /// <remarks/>
        public string AppId
        {
            get
            {
                return this.appIdField;
            }
            set
            {
                this.appIdField = value;
            }
        }

        /// <remarks/>
        public double Latitude
        {
            get
            {
                return this.latitudeField;
            }
            set
            {
                this.latitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LatitudeSpecified
        {
            get
            {
                return this.latitudeFieldSpecified;
            }
            set
            {
                this.latitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Longitude
        {
            get
            {
                return this.longitudeField;
            }
            set
            {
                this.longitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LongitudeSpecified
        {
            get
            {
                return this.longitudeFieldSpecified;
            }
            set
            {
                this.longitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Radius
        {
            get
            {
                return this.radiusField;
            }
            set
            {
                this.radiusField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool RadiusSpecified
        {
            get
            {
                return this.radiusFieldSpecified;
            }
            set
            {
                this.radiusFieldSpecified = value;
            }
        }
    }

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]
    public enum WebSearchOption
    {

        /// <remarks/>
        DisableHostCollapsing,

        /// <remarks/>
        DisableQueryAlterations,
    }
}
```

## <a name="errors-and-warnings"></a>Erreurs et avertissements
 Les erreurs et les avertissements rencontrés lors de l'analyse du schéma XSD apparaissent comme des erreurs et des avertissements de build.

## <a name="interface-inheritance"></a>Héritage de l'interface
 Il n'est pas possible d'utiliser l'héritage de l'interface avec un développement Contrat en premier ; cela est cohérent avec la façon dont les interfaces se comportent dans d'autres opérations. Afin d’utiliser une interface qui hérite d’une interface de base, utilisez deux points de terminaison distincts. Le premier point de terminaison utilise le contrat hérité et le second implémente l’interface de base.
