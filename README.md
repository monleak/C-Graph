# Thư viện C-Graph
Đây là chức năng và ý nghĩa của các biến truyền vào. Để hiểu rõ cách dùng có thể xem Demo-cgraph

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
#### Lệnh thêm đỉnh vào danh sách vector từ 1 mảng
`cgraph_ivec_t cgraph_ivec_from_array(CGRAPH_INTEGER *a,
                                    CGRAPH_INTEGER n);`
```
CGRAPH_INTEGER *a  //mảng chứa giá trị
CGRAPH_INTEGER n  //số phần từ trong mảng
```
#### Lệnh in vector
`int cgraph_ivec_print(cgraph_ivec_t const v);`
#### Lệnh giải phóng vector
`int cgraph_ivec_free(cgraph_ivec_t *v);`
#### Lệnh thêm cạnh vào danh sách vector
`int cgraph_add_edges(cgraph_t *graph, cgraph_ivec_t const edges)`
```
cgraph_t *graph  //địa chỉ biến đồ thị
cgraph_ivec_t const edges  //các cạnh muốn thêm
```
#### Lệnh giải phóng biến đồ thị
`void cgraph_destroy(cgraph_t *graph);`
```
cgraph_t *graph  //truyền vào địa chỉ biến đồ thị
```
#### Kiểm tra đồ thị có hướng hay vô hướng
`bool cgraph_is_directed(const cgraph_t *graph);`
#### Cấu trúc của 1 biến đồ thị
```
typedef struct cgraph_s {
    CGRAPH_INTEGER n;    //số lượng đỉnh
    bool directed;     // có hướng hay không (true/false)
    cgraph_ivec_t from;  //cột đầu tiên của danh sách cạnh
    cgraph_ivec_t to;    //cột thứ 2 của danh sách cạnh
    cgraph_ivec_t oi;    //chỉ số của cạnh theo cột thứ nhất
    cgraph_ivec_t ii;   //chỉ só của cạnh theo cột thứ 2
    cgraph_ivec_t os;
    cgraph_ivec_t is;
    void *attr;
} cgraph_t;
//Giải thích: Có 1 danh sách cạnh
    0, 1,
    0, 3,
    1, 2,
    1, 3,
    2, 4,
    0, 2,
    3, 5,
    3, 1,
    1, 4
Ta có:
n = 6
directed = true
from  = {0, 0, 1, 1, 2, 0, 3, 3, 1}
to    = {1, 3, 2, 3, 4, 2, 5, 1, 4}
chỉ số   0  1  2  3  4  5  6  7  8    //chỉ số cạnh này sẽ dùng ở oi và ii
oi    = {0, 5, 1, 2, 3, 8, 4, 7, 6}   //sắp xếp theo đầu ra lần lươt từ đỉnh 0->5
ii    = {0, 7, 5, 2, 1, 3, 8, 4, 6}   //sắp xếp theo đầu vào lần lươt từ đỉnh 0->5
os    = {0, 3, 6, 7, 9, 9, 9}      //VD bậc ra của đỉnh i bằng os[i+1]-os[i]
is    = {0, 0, 2, 4, 6, 8, 9}      // bậc vào của đỉnh i bằng is[i+1]-is[i]
```
