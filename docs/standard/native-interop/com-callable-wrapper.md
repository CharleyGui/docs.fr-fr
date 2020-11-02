---
title: Wrapper pouvant être appelé par COM
description: Lorsqu’un client COM appelle un objet .NET, le CLR crée l’objet managé et un wrapper CCW (COM Callable Wrapper) pour celui-ci. Les clients COM appellent le wrapper pour l’objet.
ms.date: 10/23/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
ms.openlocfilehash: cc27ba47c88d424a80eb47aaa310bdfd6d18433a
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187916"
---
# <a name="com-callable-wrapper"></a>Wrapper pouvant être appelé par COM

Quand un client COM appelle un objet .NET, le common language runtime crée l'objet managé et un wrapper CCW pour cet objet. Parce qu'ils ne peuvent pas référencer directement un objet .NET, les clients COM utilisent le wrapper CCW en tant que proxy pour l'objet managé.

Le runtime crée un unique wrapper CCW pour un objet managé, indépendamment du nombre de clients COM demandant ses services. Comme le montre l'illustration suivante, plusieurs clients COM peuvent contenir une référence au wrapper CCW qui expose l'interface INew. Le wrapper CCW contient quant à lui une référence à l'objet managé qui implémente l'interface et fait l'objet d'un garbage collection. Les clients COM et .NET peuvent envoyer simultanément des requêtes au même objet managé.

![Plusieurs clients COM contenant une référence au wrapper CCW qui expose INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

Les wrappers CCW ne sont pas visibles par les autres classes qui s’exécutent dans le runtime .NET. Leur objectif principal est de marshaler les appels entre code managé et code non managé. Cependant, les wrappers CCW gèrent également l'identité et la durée de vie des objets managés qu'ils encapsulent.

## <a name="object-identity"></a>Identité d'un objet

Le runtime alloue de la mémoire pour l'objet .NET depuis son tas collecté, ce qui permet au runtime de déplacer l'objet au sein de la mémoire selon les besoins. En revanche, le runtime alloue de la mémoire pour le wrapper CCW depuis un tas non collecté, permettant ainsi aux clients COM de faire directement référence au wrapper.

## <a name="object-lifetime"></a>Durée de vie des objets

Contrairement au client .NET qu'il encapsule, le wrapper CCW fait l'objet d'un comptage de références comme dans COM. Quand le nombre de références du wrapper CCW atteint zéro, le wrapper libère sa référence à l'objet managé. Un objet managé sans aucune référence restante sera collecté lors du prochain cycle de garbage collection.

## <a name="simulating-com-interfaces"></a>Simulation d'interfaces COM

CCW expose aux clients COM l’ensemble des interfaces, types de données et valeurs de retour publics et visibles par COM d’une manière qui est cohérente avec l’application de COM de l’interaction reposant sur l’interface. Pour un client COM, l’appel de méthodes sur un objet .NET est identique à l’appel de méthodes sur un objet COM.

Pour adopter cette approche transparente, le wrapper CCW fabrique des interfaces COM classiques, comme **IUnknown** et **IDispatch** . Comme le montre l'illustration suivante, le wrapper CCW contient une référence unique sur l'objet .NET qu'il encapsule. Le client COM et l’objet .NET interagissent via le proxy et la construction stub du wrapper CCW.

![Diagramme illustrant la façon dont le wrapper CCW fabrique des interfaces COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

Outre l’exposition des interfaces qui sont implémentées explicitement par une classe dans l’environnement managé, le runtime .NET fournit également des implémentations des interfaces COM répertoriées dans le tableau suivant, pour le compte de l’objet. Une classe .NET peut substituer le comportement par défaut par sa propre implémentation de ces interfaces. Toutefois, le runtime fournit toujours l’implémentation pour les interfaces **IUnknown** et **IDispatch** .

|Interface|Description|
|---------------|-----------------|
|**IDispatch**|Fournit un mécanisme de liaison tardive au type.|
|**IErrorInfo**|Fournit une description textuelle de l’erreur, sa source, un fichier d’aide, un contexte d’aide et le GUID de l’interface ayant défini l’erreur (toujours **GUID_NULL** pour les classes .NET).|
|**IProvideClassInfo**|Permet aux clients COM d’accéder à l’interface **ITypeInfo** implémentée par une classe managée. Retourne `COR_E_NOTSUPPORTED` sur .NET Core pour les types non importés à partir de COM. |
|**ISupportErrorInfo**|Permet à un client COM de déterminer si l’objet managé prend en charge l’interface **IErrorInfo** . Dans ce cas, il permet au client d'obtenir un pointeur vers le dernier objet exception. Tous les types managés prennent en charge l’interface **IErrorInfo** .|
|**ITypeInfo** (.NET Framework uniquement)|Fournit des informations de type pour une classe qui sont les mêmes que celles fournies par Tlbexp.exe.|
|**IUnknown**|Fournit l’implémentation standard de l’interface **IUnknown** avec laquelle le client COM gère la durée de vie du wrapper CCW et fournit le forçage de type.|

 Une classe managée peut également fournir les interfaces COM décrites dans le tableau suivant.

|Interface|Description|
|---------------|-----------------|
|L’interface de classe ( \_ *className* )|Interface, exposée par le runtime et non définie explicitement, qui expose l'ensemble des interfaces, méthodes, propriétés et champs publics qui sont exposés explicitement sur un objet managé.|
|**IConnectionPoint** et **IConnectionPointContainer**|Interface pour les objets qui émettent des événements basés sur les délégués (interface pour l'inscription des abonnés d'événements).|
|**IDispatchEx** (.NET Framework uniquement)|Interface fournie par le runtime si la classe implémente **IExpando** . L’interface **IDispatchEx** est une extension de l’interface **IDispatch** qui, contrairement à l’interface **IDispatch** , permet l’énumération, l’ajout, la suppression et l’appel de la casse des membres.|
|**IEnumVARIANT**|Interface pour les classes de type collection, qui énumère les objets d’une collection si la classe implémente **IEnumerable** .|

## <a name="introducing-the-class-interface"></a>Présentation de l'interface de classe

L'interface de classe, qui n'est pas explicitement définie dans le code managé, est une interface qui expose l'ensemble des méthodes, propriétés, champs et événements publics qui sont exposés explicitement sur l'objet .NET. Cette interface peut être double ou dispatch uniquement. L'interface de classe reçoit le nom de la classe .NET, précédé d'un trait de soulignement. Par exemple, pour la classe Mammal, l’interface de classe est \_Mammal.

Pour les classes dérivées, l'interface de classe expose l'ensemble des méthodes, propriétés et champs publics de la classe de base. La classe dérivée expose également une interface de classe pour chaque classe de base. Par exemple, si la classe Mammal étend la classe MammalSuperclass, qui elle-même étend System.Object, l’objet .NET expose aux clients COM trois interfaces de classe nommées \_Mammal, \_MammalSuperclass et \_Object.

Regardons, par exemple, la classe .NET suivante :

```vb
' Applies the ClassInterfaceAttribute to set the interface to dual.
<ClassInterface(ClassInterfaceType.AutoDual)> _
' Implicitly extends System.Object.
Public Class Mammal
    Sub Eat()
    Sub Breathe()
    Sub Sleep()
End Class
```

```csharp
// Applies the ClassInterfaceAttribute to set the interface to dual.
[ClassInterface(ClassInterfaceType.AutoDual)]
// Implicitly extends System.Object.
public class Mammal
{
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

Le client COM peut obtenir un pointeur vers une interface de classe nommée `_Mammal`. Sur .NET Framework, vous pouvez utiliser l’outil [Exportateur de bibliothèques de types (Tlbexp. exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) pour générer une bibliothèque de types contenant la définition de l’interface `_Mammal`. L’exportateur de bibliothèques de types n’est pas pris en charge sur .NET Core. Si la classe `Mammal` implémentait une ou plusieurs interfaces, les interfaces apparaîtraient sous la coclasse.

```console
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]
interface _Mammal : IDispatch
{
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*
        pRetVal);
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]
        VARIANT_BOOL* pRetVal);
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);
    [id(0x6002000d)] HRESULT Eat();
    [id(0x6002000e)] HRESULT Breathe();
    [id(0x6002000f)] HRESULT Sleep();
}
[uuid(…)]
coclass Mammal
{
    [default] interface _Mammal;
}
```

La génération de l'interface de classe est facultative. Par défaut, COM Interop génère une interface de dispatch pour chaque classe que vous exportez vers une bibliothèque de types. Vous pouvez empêcher ou modifier la création automatique de cette interface en appliquant <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> à votre classe. Même si l'interface de classe simplifie l'exposition des classes managées à COM, ses utilisations sont limitées.

> [!CAUTION]
> L'utilisation de l'interface de classe, au lieu de définir explicitement la vôtre, peut compliquer le contrôle de version de votre classe managée. Lisez les instructions suivantes avant d'utiliser l'interface de classe.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Définissez une interface explicite pour les clients COM plutôt que de générer l'interface de classe.

Étant donné que COM Interop génère automatiquement une interface de classe, les modifications après version apportées à votre classe peuvent modifier la disposition de l'interface de classe exposée par le common language runtime. Étant donné que les clients COM ne sont généralement pas préparés à gérer les modifications apportées à la disposition d'une interface, ils s'arrêtent si vous modifiez la disposition des membres de la classe.

Cette règle renforce l'idée que les interfaces exposées aux clients COM doivent rester intactes. Pour réduire le risque d'arrêt des clients COM en réorganisant par inadvertance la disposition de l'interface, isolez toutes les modifications apportées à la classe à partir de la disposition de l'interface en définissant explicitement les interfaces.

Utilisez **ClassInterfaceAttribute** pour désactiver la génération automatique de l’interface de classe et implémenter une interface explicite de la classe, comme dans le fragment de code suivant :

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

La valeur **ClassInterfaceType.None** empêche l’interface de classe d’être générée quand les métadonnées de classe sont exportées vers une bibliothèque de types. Dans l'exemple précédent, les clients COM peuvent accéder à la classe `LoanApp` uniquement via l'interface `IExplicit`.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Éviter de mettre en cache des identificateurs de dispatch (DISPID)

L'utilisation de l'interface de classe est une option acceptable pour les clients par script, les clients Microsoft Visual Basic 6.0 ou tout client à liaison tardive qui ne met pas en cache les DISPID des membres d'interface. Les DISPID identifient les membres d’interface pour permettre la liaison tardive.

Pour l'interface de classe, la génération de DISPID repose sur la position du membre de l'interface. Si vous modifiez l'ordre du membre et exportez la classe vers une bibliothèque de types, vous modifierez les DISPID générés dans l'interface de classe.

Pour éviter l’arrêt des clients COM à liaison tardive lors de l’utilisation de l’interface de classe, appliquez **ClassInterfaceAttribute** avec la valeur **ClassInterfaceType.AutoDispatch** . Cette valeur implémente une interface de classe de dispatch, mais omet la description de l'interface de la bibliothèque de types. Sans description d'interface, les clients sont incapables de mettre en cache les DISPID au moment de la compilation. Même s'il s'agit du type d'interface par défaut pour l'interface de classe, vous pouvez appliquer explicitement la valeur d'attribut.

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

Pour obtenir le DISPID d’un membre d’interface au moment de l’exécution, les clients COM peuvent appeler **IDispatch.GetIdsOfNames** . Pour appeler une méthode sur l’interface, passez le DISPID retourné comme argument à **IDispatch.Invoke** .

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Limitez l'utilisation de l'option d'interface double pour l'interface de classe.

Les interfaces doubles permettent une liaison anticipée et tardive aux membres d’interface par les clients COM. Au moment du design et au cours des tests, il peut s'avérer utile de faire de l'interface de classe une interface double. Pour une classe managée (et ses classes de base) qui ne sera jamais modifiée, cette option est également acceptable. Dans tous les autres cas, évitez d'utiliser l'interface double.

Une interface double générée automatiquement peut être appropriée dans de rares cas. Toutefois, cela rend souvent le contrôle de version plus complexe. Par exemple, les clients COM qui utilisent l'interface de classe d'une classe dérivée peuvent facilement s'arrêter en raison des modifications apportées à la classe de base. Quand une tierce partie fournit la classe de base, la disposition de l'interface de classe est hors de votre contrôle. De plus, contrairement à une interface Dispatch uniquement, une interface Dual ( **ClassInterfaceType.AutoDual** ) offre une description de l’interface de classe dans la bibliothèque de types exportée. Une telle description encourage les clients à liaison tardive à mettre en cache les DISPID au moment de la compilation.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Vérifiez que toutes les notifications d’événements COM sont à liaison tardive.

Par défaut, les informations du type COM sont intégrées directement aux assemblys managés, ce qui éviter d’avoir à utiliser des assemblys PIA (Primary Interop Assembly). Les informations de type incorporées présentent toutefois une limitation : elles ne prennent pas en charge la distribution des notifications d’événements COM par des appels vtable à liaison anticipée, mais seulement par des appels `IDispatch::Invoke` à liaison tardive.

Si votre application exige des appels à liaison anticipée à des méthodes d’interface d’événements COM, vous pouvez définir la propriété **Incorporer les types Interop** sur `true` dans Visual Studio, ou inclure l’élément suivant dans votre fichier projet :

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Wrappers COM](com-wrappers.md)
- [Exposition de composants .NET Framework à COM](../../framework/interop/exposing-dotnet-components-to-com.md)
- [Exposition de composants .NET Core à COM](../../core/native-interop/expose-components-to-com.md)
- [Qualification des types .NET pour l’interopérabilité](qualify-net-types-for-interoperation.md)
- [Wrapper pouvant être appelé par le runtime](runtime-callable-wrapper.md)
