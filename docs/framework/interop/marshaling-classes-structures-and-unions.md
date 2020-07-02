---
title: Marshaling de classes, de structures, et d'unions
description: Examinez comment marshaler des classes, des structures et des unions. Affichez des exemples de classes de marshaling, des structures avec des structures imbriquées, des tableaux de structures et des unions.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: 5e616b5bb513939cadd8fe5c72675ba0b6e070a3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621520"
---
# <a name="marshaling-classes-structures-and-unions"></a>Marshaling de classes, de structures, et d'unions

Les classes et les structures sont similaires dans .NET Framework. Elles peuvent toutes deux posséder des champs, des propriétés et des événements. Elles peuvent également posséder des méthodes statiques et non statiques. Une différence notable existe toutefois : les structures sont des types valeur et les classes sont des types référence.

Le tableau suivant répertorie les options de marshaling pour les classes, les structures et les unions. Il décrit leur utilisation et fournit un lien vers l'exemple d'appel de code non managé correspondant.

|Type|Description|Exemple|
|----------|-----------------|------------|
|Classe par valeur.|Passe une classe avec des membres entiers en tant que paramètre In/Out, comme le cas managé.|[SysTime (exemple)](#systime-sample)|
|Structure par valeur.|Passe des structures en tant que paramètres In.|[Exemple de structures](#structures-sample)|
|Structure par référence.|Passe des structures en tant que paramètres In/Out.|[OSInfo (exemple)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|
|Structure avec structures imbriquées (aplaties).|Passe une classe représentant une structure avec structures imbriquées dans la fonction non managée. La structure est aplatie sous la forme d'une même grande structure dans le prototype managé.|[FindFile (exemple)](#findfile-sample)|
|Structure avec un pointeur vers une autre structure.|Passe une structure contenant un pointeur vers une autre structure en tant que membre.|[Exemple structures](#structures-sample)|
|Tableau de structures avec des entiers par valeur.|Passe un tableau de structures contenant uniquement des entiers en tant que paramètre In/Out. Les membres du tableau peuvent être modifiés.|[Arrays, exemple](marshaling-different-types-of-arrays.md)|
|Tableau de structures avec des entiers et des chaînes par référence.|Passe un tableau de structures contenant des entiers et des chaînes en tant que paramètre Out. La fonction appelée alloue de la mémoire pour le tableau.|[OutArrayOfStructs, exemple](#outarrayofstructs-sample)|
|Unions avec types valeur.|Passe des unions avec des types valeur (entier et double).|[Unions (exemple)](#unions-sample)|
|Unions avec types mixtes.|Passe des unions avec des types mixtes (entier et chaîne).|[Unions (exemple)](#unions-sample)|
|Structure avec une disposition spécifique à la plateforme.|Passe un type avec des définitions de compression natives.|[Exemple de plateforme](#platform-sample)|
|Valeurs Null dans la structure.|Passe une référence null (**Nothing** en Visual Basic) au lieu d’une référence à un type valeur.|[HandleRef (exemple)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))|

## <a name="structures-sample"></a>Exemple de structures

Cet exemple montre comment passer une structure qui pointe vers une autre structure, comment passer une structure avec structure incorporée et comment passer une structure avec tableau incorporé.  
  
L'exemple Structures utilise les fonctions non managées ci-dessous, accompagnées de leur déclaration de fonction d'origine :

- **TestStructInStruct** exportée depuis PinvokeLib.dll.

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- **TestStructInStruct3** exportée depuis PinvokeLib.dll.

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- **TestArrayInStruct** exportée depuis PinvokeLib.dll.

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) est une bibliothèque non managée personnalisée qui contient des implémentations des fonctions précédemment répertoriées, ainsi que quatre structures : **MYPERSON**, **MYPERSON2**, **MYPERSON3** et **MYARRAYSTRUCT**. Ces structures contiennent les éléments suivants :

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

Les structures managées `MyPerson`,`MyPerson2`, `MyPerson3` et `MyArrayStruct` ont les caractéristiques suivantes :

- `MyPerson` contient uniquement des membres de type chaîne. Le champ [CharSet](specifying-a-character-set.md) affecte le format ANSI aux chaînes quand elles sont passées à la fonction non managée.

- `MyPerson2`contient un **IntPtr** à la `MyPerson` structure. Le type **IntPtr** remplace le pointeur d’origine vers la structure non managée, car les applications .NET Framework n’utilisent pas de pointeurs, sauf si le code est marqué comme étant **unsafe**.

- `MyPerson3` contient `MyPerson` comme structure incorporée. Une structure incorporée dans une autre structure peut être aplatie en plaçant les éléments de la structure incorporée directement dans la structure principale. Elle peut également être conservée comme une structure incorporée, comme dans cet exemple.

- `MyArrayStruct` contient un tableau d'entiers. L’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> définit la valeur d’énumération <xref:System.Runtime.InteropServices.UnmanagedType> sur **ByValArray**, qui est utilisée pour indiquer le nombre d’éléments du tableau.

Pour toutes les structures de cet exemple, l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est appliqué pour garantir que les membres soient classés de manière séquentielle dans la mémoire, dans l'ordre dans lequel ils apparaissent.

La classe `NativeMethods` contient des prototypes managés pour les méthodes `TestStructInStruct`, `TestStructInStruct3` et `TestArrayInStruct` appelées par la classe `App`. Chaque prototype déclare un seul paramètre de la manière suivante :

- `TestStructInStruct` déclare une référence au type `MyPerson2` comme son paramètre.

- `TestStructInStruct3` déclare le type `MyPerson3` en tant que paramètre et passe le paramètre par valeur.

- `TestArrayInStruct` déclare une référence au type `MyArrayStruct` comme son paramètre.

Les structures en tant qu’arguments de méthodes sont passées par valeur, sauf si le paramètre contient le mot clé **ref** (**ByRef** dans Visual Basic). Par exemple, la méthode `TestStructInStruct` passe une référence (la valeur d'une adresse) à un objet de type `MyPerson2` au code non managé. Pour manipuler la structure vers laquelle pointe `MyPerson2`, l'exemple crée une mémoire tampon d'une taille spécifiée et retourne son adresse en combinant les méthodes <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>. Ensuite, l'exemple copie le contenu de la structure managée vers la mémoire tampon non managée. Enfin, l'exemple utilise la méthode <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> pour marshaler des données à partir de la mémoire tampon non managée vers un objet managé, ainsi que la méthode <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> pour libérer le bloc de mémoire non managé.

### <a name="declaring-prototypes"></a>Déclaration de prototypes

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a>Appel de fonctions

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a>FindFile (exemple)

Cet exemple montre comment passer une structure qui contient une autre structure incorporée à une fonction non managée. Il montre également comment utiliser l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> pour déclarer un tableau de longueur fixe au sein de la structure. Dans cet exemple, les éléments de la structure incorporée sont ajoutés à la structure parent. Pour obtenir un exemple de structure incorporée non aplatie, consultez [Exemples de structures](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).

L'exemple FindFile utilise la fonction non managée ci-dessous, accompagnée de sa déclaration de fonction d'origine :

- **FindFirstFile** exportée depuis Kernel32.dll.

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

La structure d'origine passée à la fonction contient les éléments suivants :

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

Dans cet exemple, la classe `FindData` contient un membre de données correspondant pour chaque élément de la structure d'origine et de la structure incorporée. À la place des deux tampons caractère d'origine, la classe substitue des chaînes. **MarshalAsAttribute** définit l’énumération <xref:System.Runtime.InteropServices.UnmanagedType> sur **ByValTStr**, qui est utilisé pour identifier les tableaux de caractères de longueur fixe inline qui apparaissent au sein des structures non managées.

La classe `NativeMethods` contient un prototype managé de la méthode `FindFirstFile`, qui passe la classe `FindData` en tant que paramètre. Le paramètre doit être déclaré avec les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute>, car les classes, qui sont des types référence, sont passées en tant que paramètres In par défaut.

### <a name="declaring-prototypes"></a>Déclaration de prototypes

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a>Appel de fonctions

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a>Unions (exemple)

Cet exemple montre comment passer des structures contenant uniquement des types valeur, ainsi que des structures contenant un type valeur et une chaîne en tant que paramètres, à une fonction non managée nécessitant une union. Une union représente un emplacement de mémoire qui peut être partagé par plusieurs variables.

L'exemple Unions utilise la fonction non managée ci-dessous, accompagnée de sa déclaration de fonction d'origine :

- **TestUnion** exportée depuis PinvokeLib.dll.

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) est une bibliothèque non managée personnalisée qui contient une implémentation de la fonction précédemment répertoriée, ainsi que deux unions, **MYUNION** et **MYUNION2**. Les unions peuvent contenir les éléments suivants :

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

Dans du code managé, les unions sont définies en tant que structures. La structure `MyUnion` contient deux types valeur comme ses membres : un entier et un double. L'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est défini pour contrôler la position précise de chaque membre de données. L'attribut <xref:System.Runtime.InteropServices.FieldOffsetAttribute> fournit la position physique des champs dans la représentation non managée d'une union. Notez que les deux membres possèdent les mêmes valeurs de décalage. Ils peuvent donc définir la même zone de mémoire.

`MyUnion2_1` et `MyUnion2_2` contiennent respectivement un type valeur (entier) et une chaîne. Dans du code managé, les types valeur et les types référence ne sont pas autorisés à se chevaucher. Cet exemple utilise la surcharge de méthode pour permettre à l'appelant d'utiliser les deux types quand il appelle la même fonction non managée. La disposition de `MyUnion2_1` est explicite et possède une valeur de décalage précise. En revanche, `MyUnion2_2` possède une disposition séquentielle, car les dispositions explicites ne sont pas autorisées avec les types référence. L’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> définit l’énumération <xref:System.Runtime.InteropServices.UnmanagedType> sur **ByValTStr**, qui est utilisé pour les tableaux de caractères de longueur fixe inline qui apparaissent au sein de la représentation non managée de l’union.

La classe `NativeMethods` contient les prototypes des méthodes `TestUnion` et `TestUnion2`. `TestUnion2` est surchargée pour déclarer `MyUnion2_1` ou `MyUnion2_2` en tant que paramètres.

### <a name="declaring-prototypes"></a>Déclaration de prototypes

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a>Appel de fonctions

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a>Exemple de plateforme

Dans certains scénarios, `struct` `union` les dispositions et peuvent différer selon la plateforme ciblée. Par exemple, considérez le [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type quand il est défini dans un scénario com :

```c++
#include <pshpack8.h> /* Defines the packing of the struct */
typedef struct _STRRET
    {
    UINT uType;
    /* [switch_is][switch_type] */ union
        {
        /* [case()][string] */ LPWSTR pOleStr;
        /* [case()] */ UINT uOffset;
        /* [case()] */ char cStr[ 260 ];
        }  DUMMYUNIONNAME;
    }  STRRET;
#include <poppack.h>
```

Les éléments ci-dessus `struct` sont déclarés avec des en-têtes Windows qui influencent la disposition de la mémoire du type. Lorsqu’ils sont définis dans un environnement géré, ces détails de disposition sont nécessaires pour interagir correctement avec le code natif.

La définition managée correcte de ce type dans un processus 32 bits est la suivante :

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 264)]
public struct STRRET_32
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(4)]
    public IntPtr pOleStr;

    [FieldOffset(4)]
    public uint uOffset;

    [FieldOffset(4)]
    public IntPtr cStr;
}
```

Sur un processus 64 bits, les décalages de taille *et* de champ sont différents. La disposition correcte est la suivante :

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 272)]
public struct STRRET_64
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(8)]
    public IntPtr pOleStr;

    [FieldOffset(8)]
    public uint uOffset;

    [FieldOffset(8)]
    public IntPtr cStr;
}
```

L’échec de la prise en compte de la disposition native dans un scénario d’interopérabilité peut entraîner des blocages aléatoires ou pire, des calculs incorrects.

Par défaut, les assemblys .NET peuvent s’exécuter à la fois dans une version 32 bits et 64 bits du Runtime .NET. L’application doit attendre jusqu’à l’exécution pour décider des définitions précédentes à utiliser.

L’extrait de code suivant montre un exemple montrant comment choisir entre la définition 32 bits et 64 bits au moment de l’exécution.

```CSharp
if (IntPtr.Size == 8)
{
    // Use the STRRET_64 definition
}
else
{
    Debug.Assert(IntPtr.Size == 4);
    // Use the STRRET_32 definition
}
```

## <a name="systime-sample"></a>SysTime (exemple)

Cet exemple montre comment passer un pointeur d'une classe à une fonction non managée qui attend un pointeur d'une structure.

L'exemple SysTime utilise la fonction non managée ci-dessous, accompagnée de sa déclaration de fonction d'origine :

- **GetSystemTime** exportée depuis Kernel32.dll.

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

La structure d'origine passée à la fonction contient les éléments suivants :

```cpp
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

Dans cet exemple, la classe `SystemTime` contient les éléments de la structure d'origine représentés en tant que membres de classe. L'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est défini pour s'assurer que les membres soient disposés en mémoire de manière séquentielle, dans l'ordre dans lequel ils apparaissent.

La classe `NativeMethods` contient un prototype managé de la méthode `GetSystemTime`, qui passe la classe `SystemTime` en tant que paramètre In/Out par défaut. Le paramètre doit être déclaré avec les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute>, car les classes, qui sont des types référence, sont passées en tant que paramètres In par défaut. Pour que l’appelant reçoive les résultats, ces [attributs directionnels](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) doivent être appliqués de manière explicite. La classe `App` crée une nouvelle instance de la classe `SystemTime` et accède à ses champs de données.

### <a name="code-samples"></a>Exemples de code

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs (exemple)

Cet exemple montre comment passer un tableau de structures contenant des entiers et des chaînes comme paramètres Out à une fonction non managée.

Cet exemple montre comment appeler une fonction native à l'aide de la classe <xref:System.Runtime.InteropServices.Marshal> et à l'aide de code unsafe.

Cet exemple utilise des fonctions wrapper et des appels de code non managé définis dans [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), également fournis dans les fichiers sources. Il utilise la fonction `TestOutArrayOfStructs` et la structure `MYSTRSTRUCT2`. La structure contient les éléments suivants :

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

La classe `MyStruct` contient un objet chaîne composé de caractères ANSI. Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> spécifie le format ANSI. `MyUnsafeStruct` est une structure contenant un type <xref:System.IntPtr> plutôt qu'une chaîne.

La classe `NativeMethods` contient la méthode de prototype surchargée `TestOutArrayOfStructs`. Si une méthode déclare un pointeur en tant que paramètre, la classe doit être marquée avec le mot clé `unsafe`. Étant donné que Visual Basic ne peut pas utiliser de code unsafe, la méthode surchargée, le modificateur unsafe et la structure `MyUnsafeStruct` ne sont pas nécessaires.

La classe `App` implémente la méthode `UsingMarshaling` qui effectue toutes les tâches nécessaires au passage du tableau. Le tableau est marqué avec le mot clé `out` (`ByRef` en Visual Basic) pour indiquer que les données passent de l'appelé à l'appelant. L'implémentation utilise les méthodes de la classe <xref:System.Runtime.InteropServices.Marshal> suivantes :

- <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> pour marshaler des données à partir de la mémoire tampon non managée vers un objet managé.

- <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> pour libérer la mémoire réservée aux chaînes de la structure.

- <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> pour libérer la mémoire réservée au tableau.

Comme mentionné précédemment, le langage C# autorise le code unsafe, contrairement à Visual Basic. Dans l'exemple C#, `UsingUnsafePointer` est une autre implémentation de méthode qui utilise des pointeurs plutôt que la classe <xref:System.Runtime.InteropServices.Marshal> pour passer le tableau contenant la structure `MyUnsafeStruct`.

### <a name="declaring-prototypes"></a>Déclaration de prototypes

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a>Appel de fonctions

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a>Voir aussi

- [Marshaling de données à l’aide de l’appel de code managé](marshaling-data-with-platform-invoke.md)
- [Marshaling de chaînes](marshaling-strings.md)
- [Marshaling de différents types de tableaux](marshaling-different-types-of-arrays.md)
