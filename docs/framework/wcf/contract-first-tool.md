---
title: Outil « Contrat en premier »
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 36e1a3e19f802ca5b74cf50f5bcd57c167e31e33
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291703"
---
# <a name="contract-first-tool"></a>Outil « Contrat en premier »
Les contrats de service doivent souvent être créés à partir de services existants. Dans .NET Framework 4.5 et plus tard, les classes de contrats de données peuvent être créées automatiquement à partir de services existants à l’aide de l’outil de premier contrat. Pour utiliser l'outil Contrat en premier, le fichier de définition de schéma XML (XSD) doit être téléchargé localement ; l'outil ne peut pas importer les contrats de données distants via HTTP.

 L’outil de premier contrat est intégré dans Visual Studio 2012 comme une tâche de construction. Les fichiers de code générés par la tâche de génération sont créés à chaque fois que le projet est généré, afin que le projet puisse facilement adopter les modifications du contrat de service sous-jacent.

 Les types de schémas que l'outil Contrat en premier peut importer sont les suivants :

```xml
<xsd:complexType>
 <xsd:simpleType>
 </xsd:simpleType>
</xsd:complexType>
```

 Les types simples ne seront pas générés s'ils sont des primitives telles que `Int16` ou `String` ; les types complexes ne seront pas générés s'ils sont de type `Collection`. Les types ne seront pas non plus générés s'ils font partie d'un autre `xsd:complexType`. Dans tous ces cas, les types seront référencés dans les types existants du projet à la place.

## <a name="adding-a-data-contract-to-a-project"></a>Ajout d'un contrat de données à un projet
 Pour utiliser l'outil Contrat en premier, le contrat de service (XSD) doit être ajouté au projet. Pour les besoins de cette présentation, le contrat suivant sera utilisé pour illustrer les fonctions Contrat en premier. Cette définition de service est un petit sous-ensemble du contrat de service utilisé par l’API de recherche de Bing.

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

 Pour ajouter le contrat de service ci-dessus au projet, cliquez à droite sur le projet et **sélectionnez Ajouter nouveau...**. Sélectionnez la définition de schéma dans le volet WCF de la boîte de dialogue Modèles et nommez le nouveau fichier SampleContract.xsd. Copiez et collez le code ci-dessus dans le mode Code du nouveau fichier.

## <a name="configuring-contract-first-options"></a>Configuration des options Contrat en premier
 Les options de premier contrat peuvent être configurées dans le menu Propriétés d’un projet WCF. Pour permettre le développement du premier contrat, sélectionnez **l’Enable XSD comme** case à cocher type de langue de définition dans la page WCF de la fenêtre des propriétés du projet.

 ![Capture d’écran des options WCF avec le développement de contrat-premier activé.](./media/contract-first-tool/contract-first-options.png)

 Pour configurer les propriétés avancées, cliquez sur le bouton Avancées.

 ![Boîte de dialogue avancée de paramètres de génération de code de contrat.](./media/contract-first-tool/advanced-contract-settings.png)

 Les paramètres avancés suivants peuvent être configurés pour la génération du code à partir des contrats. Les paramètres peuvent être configurés pour tous les fichiers du projet ; les paramètres ne peuvent pas être configurés pour les fichiers individuels à ce stade.

- **Mode Serializer**: Ce paramètre détermine quel sérialisateur est utilisé pour la lecture des fichiers contractuels de service. Lorsque **XML Serializer** est sélectionné, les options **Type de collection** et de **réutilisation** sont désactivées. Ces options ne s’appliquent qu’au **Serializer contrat de données**.

- **Types de réutilisation**: Ce paramètre précise quelles bibliothèques sont utilisées pour la réutilisation de type. Ce paramètre ne s’applique que si **le mode Serializer** est réglé sur **Data Contract Serializer**.

- **Type de collection**: Ce paramètre spécifie le type entièrement qualifié ou qualifié d’assemblage à utiliser pour le type de données de collecte. Ce paramètre ne s’applique que si **le mode Serializer** est réglé sur **Data Contract Serializer**.

- **Type de dictionnaire**: Ce paramètre spécifie le type entièrement qualifié ou qualifié d’assemblage à utiliser pour le type de données du dictionnaire.

- **EnableDataBinding**: Ce paramètre précise <xref:System.ComponentModel.INotifyPropertyChanged> s’il faut implémenter l’interface sur tous les types de données pour implémenter la liaison des données.

- **ExclusTypes**:Ce paramètre spécifie la liste des types entièrement qualifiés ou qualifiés pour l’assemblage à exclure des assemblées référencées. Ce paramètre ne s’applique que si **le mode Serializer** est réglé sur **Data Contract Serializer**.

- **GenerateInternalTypes**: Ce cadre précise s’il faut générer des classes qui sont marquées comme internes. Ce paramètre ne s’applique que si **le mode Serializer** est réglé sur **Data Contract Serializer**.

- **GenerateSerializableTypes**: Ce paramètre précise s’il faut générer des classes avec l’attribut. <xref:System.SerializableAttribute> Ce paramètre ne s’applique que si **le mode Serializer** est réglé sur **Data Contract Serializer**.

- **ImportXMLTypes**: Ce paramètre précise s’il faut configurer le sérialisateur du contrat de données pour appliquer l’attribut <xref:System.SerializableAttribute> aux classes sans l’attribut. <xref:System.Runtime.Serialization.DataContractAttribute>  Ce paramètre ne s’applique que si **le mode Serializer** est réglé sur **Data Contract Serializer**.

- **SupportFx35TypedDataSets**: Ce paramètre précise s’il convient de fournir des fonctionnalités supplémentaires pour les ensembles de données typés créés pour .NET Framework 3.5. Lorsque **le mode Serializer** est réglé <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> sur **XML Serializer**, l’extension sera ajoutée à l’importateur de schémas XML lorsque cette valeur est définie à True. Lorsque **le mode Serializer** est réglé sur <xref:System.DateTimeOffset> Data Contract **Serializer**, le type sera exclu <xref:System.DateTimeOffset> des Références lorsque cette valeur est définie à False, de sorte qu’un est toujours généré pour les anciennes versions-cadres.

- **InputXsdFiles**: Ce paramètre spécifie la liste des fichiers d’entrée. Chaque fichier doit contenir un schéma XML valide.

- **Langue**: Ce paramètre spécifie la langue du code contractuel généré. Le paramètre doit être reconnaissable par <xref:System.CodeDom.Compiler.CodeDomProvider>.

- **NamespaceMappings**: Ce paramètre spécifie les cartographies des espaces de noms de cibles XSD aux espaces de noms CLR. Chaque mappage doit utiliser le format suivant :

    ```xml
    "Schema Namespace, CLR Namespace"
    ```

     Le sérialiseur XML n'accepte qu'un seul mappage au format suivant :

    ```xml
    "*, CLR Namespace"
    ```

- **OutputDirectory**: Ce paramètre précise l’annuaire où les fichiers de code seront générés.

 Les paramètres seront utilisés pour générer des types de contrat de service à partir des fichiers de contrat de service lorsque le projet est généré.

## <a name="using-contract-first-development"></a>Utilisation du développement Contrat en premier
 Après avoir ajouté le contrat de service au projet et confirmé les paramètres de construction, construire le projet en appuyant sur **F6**. Les types définis dans le contrat de service sont ensuite disponibles dans le projet.

 Pour utiliser les types définis dans le contrat de service, ajoutez une référence à `ContractTypes` sous l'espace de noms actuel :

```csharp
using MyProjectNamespace.ContractTypes;
```

 Les types définis dans le contrat de service seront alors résolvables dans le projet, comme indiqué ci-dessous :

 ![Classe SearchRequest montrant dans IntelliSense après avoir tapé les premières lettres.](./media/contract-first-tool/service-contract-types.png)

 Les types générés par l'outil sont créés dans le fichier GeneratedXSDTypes.cs. Le fichier est \<créé dans l’annuaire du projet\<>/obj/ configuration de construction>/XSDGeneratedCode/ directory par défaut. Le schéma de l’échantillon au début de cet article est converti comme suit:

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
