# Thư viện C-Graph

#### Lệnh in ra bậc vào ra của đỉnh
`int cgraph_degree_one(const cgraph_t *graph,
                      CGRAPH_INTEGER *res,
                      const CGRAPH_INTEGER node,
                      cgraph_neimode_t mode,
                      bool loops);`
```
const cgraph_t *graph   // địa chỉ của biến cgraph (cgraph_t B => truyền vào &B)
CGRAPH_INTEGER *res   // biến sẽ nhận giá trị bậc vào/ra của đỉnh
const CGRAPH_INTEGER node   // đỉnh cần xác định bậc vào/ra
cgraph_neimode_t mode   // chế độ vào/ra (CGRAPH_OUT/CGRAPH_IN)
bool loops   // đồ thị có hướng hay không (true/false)
```
