asdfsdf

{%hackmd @yukaii/hackfoldr-book-mode-theme %}

```typescript=
const EDITABLE_VARIABLES = {
  [REQUEST_VARIABLE_ID.gender]: true,
  [REQUEST_VARIABLE_ID.age]: true,
  [REQUEST_VARIABLE_ID.accidentRecord]: true,
  [REQUEST_VARIABLE_ID.carModel]: true,
  [REQUEST_VARIABLE_ID.year]: true,
}

export const useVariableMeta = (
  groups: VariableGroup[],
  groupSelectMap: GroupSelectMap,
): VariableMeta[] => {
  const variablesMeta = useBaseVariableMeta(groups, groupSelectMap)
  const newVariablesMeta = useMemo(
    () =>
      variablesMeta.map((meta) => ({
        ...meta,
        visible:
          meta.visible &&
          groupSelectMap[meta.gid].checked &&
          EDITABLE_VARIABLES[meta.id],
      })),
    [variablesMeta, groupSelectMap],
  )

  return newVariablesMeta
}
```