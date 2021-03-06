---
title: 'Procédure : regrouper des éléments dans un contrôle ListView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: b4cd2b9ed23f377912270d33b1415ad39c9e80c0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966629"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Procédure : regrouper des éléments dans un contrôle ListView Windows Forms
Avec la fonctionnalité de regroupement du <xref:System.Windows.Forms.ListView> contrôle, vous pouvez afficher des jeux d’éléments associés dans des groupes. Ces groupes sont séparés sur l’écran par des en-têtes de groupe horizontaux qui contiennent les titres des groupes. Vous pouvez utiliser <xref:System.Windows.Forms.ListView> des groupes pour faciliter la navigation dans des listes volumineuses en regroupant les éléments par ordre alphabétique, par date ou par tout autre regroupement logique. L’illustration suivante montre des éléments groupés.  
  
 ![Capture d’écran des groupes de ListView impaires et pairs.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  
   
 Pour activer le regroupement, vous devez d’abord créer un ou plusieurs groupes dans le concepteur ou par programme. Une fois qu’un groupe a été défini, vous <xref:System.Windows.Forms.ListView> pouvez assigner des éléments à des groupes. Vous pouvez également déplacer des éléments d’un groupe à un autre par programmation.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ListView>les groupes sont disponibles uniquement [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] sur lorsque votre application appelle <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> la méthode. Sur les systèmes d’exploitation antérieurs, tout code relatif aux groupes n’a aucun effet et les groupes n’apparaissent pas. Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Pour ajouter des groupes  
  
1. Utilisez la méthode <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> de la collection <xref:System.Windows.Forms.ListView.Groups%2A> .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Pour supprimer des groupes  
  
1. Utilisez la <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> méthode <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> ou de la <xref:System.Windows.Forms.ListView.Groups%2A> collection.  
  
     La <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> méthode supprime un seul groupe; la <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> méthode supprime tous les groupes de la liste.  
  
    > [!NOTE]
    > La suppression d’un groupe ne supprime pas les éléments de ce groupe.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Pour affecter des éléments à des groupes ou déplacer des éléments entre des groupes  
  
1. Définissez la <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> propriété des éléments individuels.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [Contrôle ListView](listview-control-windows-forms.md)
- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour Ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
