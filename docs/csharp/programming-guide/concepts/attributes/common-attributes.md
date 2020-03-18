---
title: Attributs courants (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399755"
---
# <a name="common-attributes-c"></a>Attributs courants (C#)
Cette rubrique décrit les attributs le plus couramment utilisés dans les programmes C#.  
  
- [Attributs globaux](#Global)  
  
- [Attribut obsolète](#Obsolete)  
  
- [Attribut Conditional](#Conditional)  
  
- [Attributs Info De l’appelant](#CallerInfo)  
  
## <a name="Global"></a> Attributs globaux  
 La plupart des attributs sont appliqués à des éléments de langage spécifiques, tels que les classes ou les méthodes. Toutefois, certains attributs sont globaux : ils s’appliquent à la totalité d’un assembly ou d’un module. Par exemple, l’attribut <xref:System.Reflection.AssemblyVersionAttribute> peut être utilisé pour incorporer des informations de version dans un assembly, de la manière suivante :  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Les attributs globaux apparaissent dans le code source après toute directive `using` de niveau supérieur et avant toute déclaration de type, de module ou d’espace de noms. Les attributs globaux peuvent apparaître dans plusieurs fichiers sources, mais les fichiers doivent être compilés en un seul passage. Dans les projets C#, les attributs globaux sont placés dans le fichier AssemblyInfo.cs.  
  
 Les attributs d’assembly sont des valeurs qui fournissent des informations sur un assembly. Ils sont répartis dans les catégories suivantes :  
  
- Attributs d’identité de l’assembly  
  
- Attributs d’informations  
  
- Attributs de manifeste de l’assembly  
  
### <a name="assembly-identity-attributes"></a>Attributs d’identité de l’assembly  
 Trois attributs (avec un nom fort, le cas échéant), déterminent l’identité d’un assembly : nom, version et culture. Ces attributs constituent le nom complet de l’assembly et sont obligatoires quand vous le référencez le code. Vous pouvez définir la version et la culture d’un assembly en utilisant des attributs. Toutefois, la valeur de nom est définie par le compilateur, l’IDE de Visual Studio dans la [boîte de dialogue Informations sur l’assembly](/visualstudio/ide/reference/assembly-information-dialog-box) ou l’utilitaire Assembly Linker (Al.exe) lors de la création de l’assembly, en fonction du fichier qui contient le manifeste de l’assembly. L’attribut <xref:System.Reflection.AssemblyFlagsAttribute> spécifie si plusieurs copies de l’assembly peuvent coexister.  
  
 Le tableau suivant présente les attributs d’identité.  
  
|Attribut|Objectif|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Décrit intégralement l’identité d’un assembly.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Spécifie la version d’un assembly.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Spécifie la culture prise en charge par l'assembly.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Spécifie si un assembly prend en charge l’exécution côte à côte sur le même ordinateur, dans le même processus ou dans le même domaine d’application.|  
  
### <a name="informational-attributes"></a>Attributs d’informations  
 Vous pouvez utiliser les attributs d’informations pour fournir des informations supplémentaires sur le produit ou la société de l’assembly. Le tableau suivant présente les attributs d’informations définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.  
  
|Attribut|Objectif|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Définit un attribut personnalisé qui spécifie un nom de produit pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Définit un attribut personnalisé qui spécifie une marque pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Définit un attribut personnalisé qui spécifie une version d’informations pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Définit un attribut personnalisé qui spécifie un nom de société pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Définit un attribut personnalisé qui spécifie un copyright pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Demande au compilateur d’utiliser un numéro de version spécifique pour la ressource de la version du fichier Win32.|  
|<xref:System.CLSCompliantAttribute>|Indique si l’assembly est conforme à la spécification CLS (Common Language Specification).|  
  
### <a name="assembly-manifest-attributes"></a>Attributs de manifeste de l’assembly  
 Vous pouvez utiliser les attributs de manifeste de l’assembly pour fournir des informations dans le manifeste de l’assembly. Cela inclut le titre, la description, l’alias par défaut et la configuration. Le tableau suivant présente les attributs de manifeste de l’assembly définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.  
  
|Attribut|Objectif|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Définit un attribut personnalisé qui spécifie un titre d’assembly pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Définit un attribut personnalisé qui spécifie une description d’assembly pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Définit un attribut personnalisé qui spécifie une configuration d’assembly (telles que retail ou debug) pour un manifeste d’assembly.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Définit un alias par défaut convivial pour un manifeste d’assembly.|  
  
## <a name="Obsolete"></a>Attribut obsolète  
 L’attribut `Obsolete` est utilisé pour marquer une entité de programme comme étant une entité dont l’utilisation n’est plus recommandée. Chaque utilisation d’une entité marquée comme obsolète génère par la suite un avertissement ou une erreur, selon la façon dont l’attribut est configuré. Par exemple :  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 Dans cet exemple, l’attribut `Obsolete` est appliqué à la classe `A` et à la méthode `B.OldMethod`. Comme le deuxième argument du constructeur d’attribut appliqué à `B.OldMethod` a la valeur `true`, l’utilisation de cette méthode entraîne une erreur du compilateur, alors que l’utilisation de la classe `A` n’entraîne qu’un avertissement. Toutefois, l’appel de `B.NewMethod` ne produit aucun avertissement ni aucune erreur.  
  
 La chaîne fournie comme premier argument au constructeur d’attribut est affichée dans l’avertissement ou dans l’erreur. Par exemple, utilisé avec les définitions précédentes, le code suivant génère deux avertissements et une erreur :  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Deux avertissements pour la classe `A` sont générés : un pour la déclaration de la référence de classe et un pour le constructeur de classe.  
  
 L’attribut `Obsolete` peut être utilisé sans arguments, mais il est recommandé d’inclure une explication sur la raison pour laquelle l’élément est obsolète et d’indiquer quoi utiliser en remplacement.  
  
 `Obsolete` est un attribut à usage unique et peut être appliqué à toute entité qui autorise des attributs. `Obsolete` est un alias pour <xref:System.ObsoleteAttribute>.  
  
## <a name="Conditional"></a>Attribut conditionnel  
 Avec l’attribut `Conditional`, l’exécution d’une méthode dépend d’un identificateur de prétraitement. L’attribut `Conditional` est un alias pour <xref:System.Diagnostics.ConditionalAttribute>, et peut être appliqué à une méthode ou une classe d’attributs.  
  
 Dans cet exemple, `Conditional` est appliqué à une méthode pour activer ou désactiver l’affichage d’informations de diagnostic spécifiques au programme :  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 Si l’identificateur `TRACE_ON` n’est pas défini, aucune sortie de trace n’est affichée.  
  
 L’attribut `Conditional` est souvent utilisé avec l’identificateur `DEBUG` pour activer la trace et enregistrer des fonctionnalités pour les versions Debug, mais pas pour les versions Release, de la manière suivante :  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Quand une méthode marquée comme conditionnelle est appelée, la présence ou l’absence du symbole de prétraitement spécifié détermine si l’appel est inclus ou omis. Si le symbole est défini, l’appel est inclus ; sinon, il est omis. `Conditional` offre une solution à la fois plus efficace, plus élégante et moins sujette aux erreurs que les méthodes englobantes contenues dans les blocs `#if…#endif`, tels que le suivant :  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Une méthode conditionnelle doit figurer dans une déclaration de classe ou de struct, et ne doit pas avoir de valeur de retour.  
  
### <a name="using-multiple-identifiers"></a>Utilisation de plusieurs identificateurs  
 Si une méthode comporte plusieurs attributs `Conditional`, un appel à cette dernière est inclus si l’un des symboles conditionnels au moins est défini (en d’autres termes, si les symboles sont liés logiquement par l’opérateur OR). Dans cet exemple, la présence de `A` ou de `B` entraîne un appel de méthode :  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Pour lier logiquement les symboles au moyen de l’opérateur AND, vous pouvez définir des méthodes conditionnelles en série. Par exemple, la deuxième méthode ci-dessous ne s’exécute que si `A` et `B` sont définis :  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a>Utilisation de Conditional avec des classes d’attributs  
 L’attribut `Conditional` peut également être appliqué à une définition de classe d’attributs. Dans cet exemple, l’attribut personnalisé `Documentation` n’ajoute des informations aux métadonnées que si DEBUG est défini.  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
## <a name="CallerInfo"></a>Attributs Info De l’appelant  
 À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode. Vous pouvez obtenir le chemin du fichier de code source, le numéro de ligne dans le code source, ainsi que le nom de membre de l’appelant.  
  
 Pour obtenir des informations de membre de l’appelant, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs. Chaque paramètre facultatif spécifie une valeur par défaut. Le tableau suivant répertorie les attributs d'informations de l'appelant définis dans l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :  
  
|Attribut|Description|Type|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Chemin d’accès complet du fichier source qui contient l’appelant. C’est le chemin au moment de la compilation.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numéro de ligne dans le fichier source à partir duquel la méthode est appelée.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nom de la méthode ou nom de la propriété de l’appelant. Pour plus d’informations, consultez [Informations relatives à l’appelant (C#)](../caller-information.md).|`String`|  
  
 Pour plus d’informations sur les attributs d’informations de l’appelant, consultez [Informations relatives à l’appelant (C#)](../caller-information.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Guide de programmation C#](../../index.md)
- [Attributs](../../../../standard/attributes/index.md)
- [Réflexion (C#)](../reflection.md)
- [Accès à des attributs à l’aide de la réflexion (C#)](./accessing-attributes-by-using-reflection.md)
