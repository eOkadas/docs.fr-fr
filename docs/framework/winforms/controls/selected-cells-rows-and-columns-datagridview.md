---
title: 'Procédure : obtenir les cellules, lignes et colonnes sélectionnées dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 25b3ed50081add77b9f522ca8e597f2b3306cb2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960513"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Procédure : obtenir les cellules, lignes et colonnes sélectionnées dans le contrôle DataGridView Windows Forms
Vous pouvez obtenir les cellules, lignes ou colonnes sélectionnées à partir d' <xref:System.Windows.Forms.DataGridView> un contrôle à l’aide des propriétés <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>correspondantes: <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>et. Dans les procédures suivantes, vous allez obtenir les cellules sélectionnées et afficher leurs index de lignes et de colonnes dans <xref:System.Windows.Forms.MessageBox>un.  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Pour obtenir les cellules sélectionnées dans un contrôle DataGridView  
  
- Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>.  
  
    > [!NOTE]
    > Utilisez la <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> méthode pour éviter d’avoir un nombre potentiellement important de cellules.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Pour obtenir les lignes sélectionnées dans un contrôle DataGridView  
  
- Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>. Pour permettre aux utilisateurs de sélectionner des lignes, vous devez <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> affecter à <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> la <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>propriété la valeur ou.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Pour obtenir les colonnes sélectionnées dans un contrôle DataGridView  
  
- Utilisez la propriété <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Pour permettre aux utilisateurs de sélectionner des colonnes, vous devez <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> affecter à <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> la <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>propriété la valeur ou.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- <xref:System.Windows.Forms.Button>les contrôles `selectedCellsButton`nommés `selectedRowsButton`, et `selectedColumnsButton`, chacun avec des gestionnaires pour l' <xref:System.Windows.Forms.Control.Click> événement attaché.  
  
- un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
- des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Text?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les collections décrites dans cette rubrique ne s’exécutent pas efficacement quand un grand nombre de cellules, de lignes ou de colonnes est sélectionné. Pour plus d’informations sur l’utilisation de ces collections avec de grandes quantités de données, consultez [meilleures pratiques pour la mise à l’échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [Sélection et utilisation du Presse-papiers avec le contrôle DataGridView Windows Forms](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
