const onCellChange = (updatedState) => {
    const startColIndex = updatedState.columns.findIndex(
      (col) => col.header === selectedHeader
    );

    const updatedColumns = updatedState.columns.map((col, idx) => {
      if (idx >= startColIndex) {
        return {
          ...col,
          cellClassName: ({ row }) =>
            row.rowIndex === selectedRowId ? "highlight-cell" : "",
        };
      }
      return {
        ...col,
        cellClassName: undefined,
      };
    });

    setState({
      ...updatedState,
      columns: updatedColumns,
    });
  };
