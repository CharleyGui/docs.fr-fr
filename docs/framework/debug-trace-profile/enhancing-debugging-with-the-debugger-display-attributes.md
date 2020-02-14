---
title: Amélioration du débogage avec les attributs d'affichage de débogueur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
ms.openlocfilehash: ca118bffb045a0e7e3a5084916a0ff8020ebda90
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216494"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Amélioration du débogage avec les attributs d'affichage de débogueur

Les attributs d’affichage de débogueur permettent au développeur du type, qui spécifie et appréhende le mieux le comportement d’exécution de ce type, de spécifier également ce à quoi le type ressemblera une fois affiché dans un débogueur. De plus, les attributs d’affichage de débogueur qui fournissent une propriété `Target` peuvent être appliqués au niveau de l’assembly par des utilisateurs sans qu’il leur soit nécessaire de connaître le code source. L’attribut <xref:System.Diagnostics.DebuggerDisplayAttribute> contrôle la façon dont un type ou un membre s’affiche dans les fenêtres de variables du débogueur. L’attribut <xref:System.Diagnostics.DebuggerBrowsableAttribute> contrôle si une classe ou un champ s’affiche dans les fenêtres de variables du débogueur et comment ils s’affichent. L’attribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> spécifie un type de substitution (ou un proxy) pour un type, et modifie le mode d’affichage de ce type dans les fenêtres de débogage. Lorsque vous affichez une variable qui a un proxy, ou type de substitution, le proxy est intégré au type d’origine dans la fenêtre d’affichage du débogueur. La fenêtre de variables du débogueur   n'affiche que les membres publics du type du proxy. Les membres privés ne sont pas affichés.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Utilisation de DebuggerDisplayAttribute  

Le constructeur <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> n’a qu’un seul argument : une chaîne à afficher dans la colonne valeur pour les instances du type. Cette chaîne peut contenir des accolades ({ et }). Le texte entre accolades est évalué comme une expression. Par exemple, le code C# suivant entraîne l’affichage de « Count = 4 » quand le signe plus (+) est sélectionné pour développer l’affichage de débogueur pour une instance de `MyHashtable`.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

Les attributs appliqués aux propriétés référencées dans l’expression ne sont pas traités. Pour le compilateur C#, une expression générale est autorisée si elle n’a qu’un accès implicite à cette référence pour l’instance actuelle du type cible. L’expression est limitée ; il n’existe aucun accès aux alias, aux variables locales ou aux pointeurs. En code C#, vous pouvez utiliser une expression générale entre accolades qui dispose d’un accès implicite au pointeur `this` uniquement pour l’instance actuelle du type cible.

Par exemple, si un objet C# a un `ToString()` substitué, le débogueur appelle la substitution et affiche son résultat au lieu du `{<typeName>}.` standard. Ainsi, si vous avez substitué `ToString()`, vous n’avez pas besoin d’utiliser <xref:System.Diagnostics.DebuggerDisplayAttribute>. Si vous utilisez les deux, l'attribut <xref:System.Diagnostics.DebuggerDisplayAttribute> prend la priorité sur la substitution de `ToString()`.

## <a name="using-the-debuggerbrowsableattribute"></a>Utilisation de DebuggerBrowsableAttribute
 Appliquez l’attribut <xref:System.Diagnostics.DebuggerBrowsableAttribute> à un champ ou une propriété pour spécifier comment il ou elle doit être affiché(e) dans la fenêtre du débogueur. Le constructeur pour cet attribut prend l’une des valeurs d’énumération <xref:System.Diagnostics.DebuggerBrowsableState>, qui spécifie l’un des états suivants :

- <xref:System.Diagnostics.DebuggerBrowsableState.Never> indique que le membre n’est pas affiché dans la fenêtre de données.  Par exemple, l’utilisation de cette valeur pour <xref:System.Diagnostics.DebuggerBrowsableAttribute> sur un champ supprime le champ de la hiérarchie ; le champ n’est pas affiché quand vous développez le type englobant en cliquant sur le signe plus (+) pour l’instance de type.

- <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indique que le membre est affiché mais n’est pas développé par défaut.  Il s'agit du comportement par défaut.

- <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indique que le membre proprement dit n’est pas affiché, mais ses objets constituants sont affichés s’il s’agit d’un tableau ou d’une collection.

> [!NOTE]
> <xref:System.Diagnostics.DebuggerBrowsableAttribute> n’est pas pris en charge par Visual Basic dans la version 2.0 du .NET Framework.

L’exemple de code suivant illustre l’utilisation du <xref:System.Diagnostics.DebuggerBrowsableAttribute> pour empêcher la propriété qui le suit d’apparaître dans la fenêtre de débogage pour la classe.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>Utilisation de DebuggerTypeProxy
 Utilisez l’attribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> quand vous avez besoin de modifier radicalement l’affichage de débogage d’un type, sans toutefois changer le type proprement dit. L’attribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> sert à spécifier un proxy d’affichage pour un type, ce qui permet à un développeur de personnaliser l’affichage en fonction du type.  Cet attribut, à l’instar de <xref:System.Diagnostics.DebuggerDisplayAttribute>, peut être utilisé au niveau de l’assembly, auquel cas la propriété <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> spécifie le type pour lequel le proxy sera utilisé. Il est généralement recommandé que cet attribut spécifie un type imbriqué privé qui se produit dans le type auquel l’attribut est appliqué.  Un évaluateur d’expression qui prend en charge les visionneuses de type vérifie la présence de cet attribut lors de l’affichage d’un type. Si l’attribut est trouvé, l’évaluateur d’expression substitue le type du proxy d’affichage pour le type auquel l’attribut est appliqué.

 Quand <xref:System.Diagnostics.DebuggerTypeProxyAttribute> est présent, la fenêtre des variables du débogueur affiche uniquement les membres publics du type de proxy. Les membres privés ne sont pas affichés. Le comportement de la fenêtre de données n’est pas modifié par les affichages améliorés par les attributs.

 Pour éviter une dégradation inutile des performances, les attributs du proxy d’affichage ne sont pas traités tant que l’objet n’est pas développé, soit par un clic de l’utilisateur sur le signe plus (+) en regard du type dans une fenêtre de données, soit par le biais de l’application de l’attribut <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Ainsi, nous vous recommandons de n’appliquer aucun attribut au type d’affichage. Les attributs peuvent et doivent être appliqués dans le corps du type d’affichage.

 L’exemple de code suivant montre comment utiliser <xref:System.Diagnostics.DebuggerTypeProxyAttribute> pour spécifier un type à utiliser en tant que proxy de l’affichage du débogueur.

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple de code suivant peut être affiché dans Visual Studio pour voir les résultats de l’application des attributs <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>et <xref:System.Diagnostics.DebuggerTypeProxyAttribute>.

### <a name="code"></a>Code

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
