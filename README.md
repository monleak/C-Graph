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

#### Lệnh in các đỉnh đi vào/đi ra của đỉnh
`int cgraph_neighbors(const cgraph_t *graph,
                     cgraph_ivec_t* neis,
                     CGRAPH_INTEGER vid,
                     cgraph_neimode_t mode);`
```
const cgraph_t *graph   // địa chỉ của biến cgraph (cgraph_t B => truyền vào &B)
cgraph_ivec_t* neis   // mảng nhận giá trị của nhứng người hàng xóm
CGRAPH_INTEGER vid   // đỉnh cần xác định
cgraph_neimode_t mode  // chế độ vào/ra (CGRAPH_OUT/CGRAPH_IN)
```
#### Lệnh khởi tạo 1 đồ thị
`int cgraph_create(cgraph_t *graph, 
                  cgraph_ivec_t const edges, 
                  CGRAPH_INTEGER n, 
                  bool directed);`
```
cgraph_t *graph   // địa chỉ của biến cgraph (cgraph_t B => truyền vào &B)
cgraph_ivec_t const edges  // các cạnh của đồ thị đó
CGRAPH_INTEGER n  // =0
bool directed  // có hướng hay không (true/false)
```
#### Lệnh khỏi tạo vector
`cgraph_ivec_create()`
```
VD: cgraph_ivec_t edges = cgraph_ivec_create();
Lệnh này để khởi tạo danh sách cạnh của đồ thị
```
#### Lệnh thêm đỉnh vào danh sách vector
`int cgraph_ivec_push_back(cgraph_ivec_t *v, CGRAPH_INTEGER value)`
```
VD: cgraph_ivec_push_back(&edges, (CGRAPH_INTEGER)A[i].ID)
```
