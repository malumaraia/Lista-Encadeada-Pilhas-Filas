#include <stdio.h>
#include <stdlib.h>

// Estrutura básica do nó
typedef struct No {
    int valor;
    struct No* prox;
} No;

// Inserir no início da lista
void inserir_inicio(No** lista, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = *lista;
    *lista = novo;
}

// Inserir no fim da lista
void inserir_fim(No** lista, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;

    if (*lista == NULL) {
        *lista = novo;
    } else {
        No* atual = *lista;
        while (atual->prox != NULL) {
            atual = atual->prox;
        }
        atual->prox = novo;
    }
}

// Função para imprimir a lista (para teste)
void imprimir_lista(No* lista) {
    while (lista != NULL) {
        printf("%d -> ", lista->valor);
        lista = lista->prox;
    }
    printf("NULL\n");
}

// Exemplo de uso
int main() {
    No* lista = NULL;

    inserir_fim(&lista, 10);
    inserir_inicio(&lista, 5);

    imprimir_lista(lista); // Saída esperada: 5 -> 10 -> NULL

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

// Estrutura do nó
typedef struct No {
    int valor;
    struct No* prox;
} No;

// Inserir no fim para montar a lista
void inserir_fim(No** lista, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;

    if (*lista == NULL) {
        *lista = novo;
    } else {
        No* atual = *lista;
        while (atual->prox != NULL)
            atual = atual->prox;
        atual->prox = novo;
    }
}

// Função para contar o número de nós
int contar_nos(No* lista) {
    int contador = 0;
    while (lista != NULL) {
        contador++;
        lista = lista->prox;
    }
    return contador;
}

// Imprimir lista (opcional para ver o que foi inserido)
void imprimir_lista(No* lista) {
    while (lista != NULL) {
        printf("%d -> ", lista->valor);
        lista = lista->prox;
    }
    printf("NULL\n");
}

// Função principal
int main() {
    No* lista = NULL;

    inserir_fim(&lista, 10);
    inserir_fim(&lista, 20);
    inserir_fim(&lista, 30);

    printf("Lista: ");
    imprimir_lista(lista);

    int total = contar_nos(lista);
    printf("Total de nós: %d\n", total); // Saída esperada: 3

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

// Estrutura do nó
typedef struct No {
    int valor;
    struct No* prox;
} No;

// Inserir no fim (para facilitar montagem da lista)
void inserir_fim(No** lista, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;

    if (*lista == NULL) {
        *lista = novo;
    } else {
        No* atual = *lista;
        while (atual->prox != NULL)
            atual = atual->prox;
        atual->prox = novo;
    }
}

// Função para buscar elemento
int buscar_elemento(No* lista, int valor) {
    while (lista != NULL) {
        if (lista->valor == valor)
            return 1;
        lista = lista->prox;
    }
    return 0;
}

// Imprimir a lista (opcional)
void imprimir_lista(No* lista) {
    while (lista != NULL) {
        printf("%d -> ", lista->valor);
        lista = lista->prox;
    }
    printf("NULL\n");
}

// Função principal
int main() {
    No* lista = NULL;

    inserir_fim(&lista, 5);
    inserir_fim(&lista, 10);
    inserir_fim(&lista, 15);

    printf("Lista: ");
    imprimir_lista(lista);

    int valor_busca = 10;
    if (buscar_elemento(lista, valor_busca)) {
        printf("Valor %d encontrado na lista.\n", valor_busca);
    } else {
        printf("Valor %d NÃO encontrado na lista.\n", valor_busca);
    }

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

// Estrutura do nó
typedef struct No {
    int valor;
    struct No* prox;
} No;

// Inserção em posição específica
void inserir_posicao(No** lista, int valor, int pos) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;

    if (pos == 0 || *lista == NULL) {
        novo->prox = *lista;
        *lista = novo;
        return;
    }

    No* atual = *lista;
    for (int i = 0; atual != NULL && i < pos - 1; i++) {
        atual = atual->prox;
    }

    if (atual == NULL) {
        free(novo); // posição inválida
        return;
    }

    novo->prox = atual->prox;
    atual->prox = novo;
}

// Inserir no fim (para montar a lista)
void inserir_fim(No** lista, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;

    if (*lista == NULL) {
        *lista = novo;
    } else {
        No* atual = *lista;
        while (atual->prox != NULL)
            atual = atual->prox;
        atual->prox = novo;
    }
}

// Imprimir a lista
void imprimir_lista(No* lista) {
    while (lista != NULL) {
        printf("%d -> ", lista->valor);
        lista = lista->prox;
    }
    printf("NULL\n");
}

// Função principal
int main() {
    No* lista = NULL;

    inserir_fim(&lista, 10);
    inserir_fim(&lista, 20);
    inserir_fim(&lista, 40);

    printf("Lista antes da inserção:\n");
    imprimir_lista(lista);

    inserir_posicao(&lista, 30, 2); // Inserir 30 na posição 2
    inserir_posicao(&lista, 5, 0);  // Inserir 5 no início

    printf("Lista após inserções:\n");
    imprimir_lista(lista);

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

// Estrutura do nó
typedef struct No {
    int valor;
    struct No* prox;
} No;

// Inserir no fim
void inserir_fim(No** lista, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;

    if (*lista == NULL) {
        *lista = novo;
    } else {
        No* atual = *lista;
        while (atual->prox != NULL)
            atual = atual->prox;
        atual->prox = novo;
    }
}

// Remover primeira ocorrência do valor
void remover_valor(No** lista, int valor) {
    No* atual = *lista;
    No* anterior = NULL;

    while (atual != NULL) {
        if (atual->valor == valor) {
            if (anterior == NULL) {
                *lista = atual->prox;
            } else {
                anterior->prox = atual->prox;
            }
            free(atual);
            return;
        }
        anterior = atual;
        atual = atual->prox;
    }
}

// Imprimir lista
void imprimir_lista(No* lista) {
    while (lista != NULL) {
        printf("%d -> ", lista->valor);
        lista = lista->prox;
    }
    printf("NULL\n");
}

// Função principal
int main() {
    No* lista = NULL;

    inserir_fim(&lista, 10);
    inserir_fim(&lista, 20);
    inserir_fim(&lista, 30);
    inserir_fim(&lista, 20);

    printf("Lista antes da remoção:\n");
    imprimir_lista(lista);

    remover_valor(&lista, 20);

    printf("Lista após remover a primeira ocorrência de 20:\n");
    imprimir_lista(lista);

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

void inserir_fim(No** lista, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;

    if (*lista == NULL) {
        *lista = novo;
    } else {
        No* atual = *lista;
        while (atual->prox != NULL)
            atual = atual->prox;
        atual->prox = novo;
    }
}

void inverter_lista(No** lista) {
    No* anterior = NULL;
    No* atual = *lista;
    No* proximo = NULL;

    while (atual != NULL) {
        proximo = atual->prox;
        atual->prox = anterior;
        anterior = atual;
        atual = proximo;
    }
    *lista = anterior;
}

void imprimir_lista(No* lista) {
    while (lista != NULL) {
        printf("%d -> ", lista->valor);
        lista = lista->prox;
    }
    printf("NULL\n");
}

int main() {
    No* lista = NULL;

    inserir_fim(&lista, 1);
    inserir_fim(&lista, 2);
    inserir_fim(&lista, 3);
    inserir_fim(&lista, 4);

    printf("Lista original:\n");
    imprimir_lista(lista);

    inverter_lista(&lista);

    printf("Lista invertida:\n");
    imprimir_lista(lista);

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

void inserir_fim(No** lista, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;

    if (*lista == NULL) {
        *lista = novo;
    } else {
        No* atual = *lista;
        while (atual->prox != NULL)
            atual = atual->prox;
        atual->prox = novo;
    }
}

// Função para encontrar o nó do meio
No* encontrar_meio(No* lista) {
    if (lista == NULL) return NULL;

    No* lento = lista;
    No* rapido = lista;

    while (rapido != NULL && rapido->prox != NULL) {
        lento = lento->prox;
        rapido = rapido->prox->prox;
    }

    return lento;
}

void imprimir_lista(No* lista) {
    while (lista != NULL) {
        printf("%d -> ", lista->valor);
        lista = lista->prox;
    }
    printf("NULL\n");
}

int main() {
    No* lista = NULL;

    inserir_fim(&lista, 10);
    inserir_fim(&lista, 20);
    inserir_fim(&lista, 30);
    inserir_fim(&lista, 40);
    inserir_fim(&lista, 50);

    printf("Lista:\n");
    imprimir_lista(lista);

    No* meio = encontrar_meio(lista);
    if (meio != NULL) {
        printf("Nó do meio: %d\n", meio->valor);
    } else {
        printf("Lista vazia\n");
    }

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

// Pilha simples usando lista encadeada
typedef struct PilhaNo {
    int valor;
    struct PilhaNo* prox;
} PilhaNo;

void push(PilhaNo** topo, int valor) {
    PilhaNo* novo = malloc(sizeof(PilhaNo));
    novo->valor = valor;
    novo->prox = *topo;
    *topo = novo;
}

int pop(PilhaNo** topo) {
    if (*topo == NULL) return -1; // Pilha vazia
    PilhaNo* temp = *topo;
    int val = temp->valor;
    *topo = temp->prox;
    free(temp);
    return val;
}

void imprimir_reversa(No* lista) {
    PilhaNo* pilha = NULL;

    while (lista != NULL) {
        push(&pilha, lista->valor);
        lista = lista->prox;
    }

    printf("Lista na ordem reversa:\n");
    while (pilha != NULL) {
        printf("%d -> ", pop(&pilha));
    }
    printf("NULL\n");
}

void inserir_fim(No** lista, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;

    if (*lista == NULL) {
        *lista = novo;
    } else {
        No* atual = *lista;
        while (atual->prox != NULL)
            atual = atual->prox;
        atual->prox = novo;
    }
}

void imprimir_lista(No* lista) {
    while (lista != NULL) {
        printf("%d -> ", lista->valor);
        lista = lista->prox;
    }
    printf("NULL\n");
}

int main() {
    No* lista = NULL;

    inserir_fim(&lista, 1);
    inserir_fim(&lista, 2);
    inserir_fim(&lista, 3);
    inserir_fim(&lista, 4);

    printf("Lista normal:\n");
    imprimir_lista(lista);

    imprimir_reversa(lista);

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

typedef struct {
    int dados[MAX];
    int topo;
} Pilha;

void inicializar(Pilha* p) {
    p->topo = -1;
}

int esta_vazia(Pilha* p) {
    return p->topo == -1;
}

int esta_cheia(Pilha* p) {
    return p->topo == MAX - 1;
}

void push(Pilha* p, int valor) {
    if (esta_cheia(p)) {
        printf("Pilha cheia!\n");
        return;
    }
    p->dados[++(p->topo)] = valor;
}

int pop(Pilha* p) {
    if (esta_vazia(p)) {
        printf("Pilha vazia!\n");
        return -1;
    }
    return p->dados[(p->topo)--];
}

int topo(Pilha* p) {
    if (esta_vazia(p)) {
        printf("Pilha vazia!\n");
        return -1;
    }
    return p->dados[p->topo];
}

int main() {
    Pilha p;
    inicializar(&p);

    push(&p, 10);
    push(&p, 20);
    push(&p, 30);

    printf("Topo da pilha: %d\n", topo(&p));

    while (!esta_vazia(&p)) {
        printf("Pop: %d\n", pop(&p));
    }

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

typedef struct {
    No* topo;
} Pilha;

void inicializar(Pilha* p) {
    p->topo = NULL;
}

int esta_vazia(Pilha* p) {
    return p->topo == NULL;
}

void push(Pilha* p, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = p->topo;
    p->topo = novo;
}

int pop(Pilha* p) {
    if (esta_vazia(p)) {
        printf("Pilha vazia!\n");
        return -1;
    }
    No* temp = p->topo;
    int val = temp->valor;
    p->topo = temp->prox;
    free(temp);
    return val;
}

int topo(Pilha* p) {
    if (esta_vazia(p)) {
        printf("Pilha vazia!\n");
        return -1;
    }
    return p->topo->valor;
}

int main() {
    Pilha p;
    inicializar(&p);

    push(&p, 5);
    push(&p, 10);
    push(&p, 15);

    printf("Topo: %d\n", topo(&p));

    while (!esta_vazia(&p)) {
        printf("Pop: %d\n", pop(&p));
    }

    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    char valor;
    struct No* prox;
} No;

typedef struct {
    No* topo;
} Pilha;

void inicializar(Pilha* p) {
    p->topo = NULL;
}

void push(Pilha* p, char valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = p->topo;
    p->topo = novo;
}

char pop(Pilha* p) {
    if (p->topo == NULL) return '\0';
    No* temp = p->topo;
    char val = temp->valor;
    p->topo = temp->prox;
    free(temp);
    return val;
}

int esta_vazia(Pilha* p) {
    return p->topo == NULL;
}

int verificar_balanceamento(char* str) {
    Pilha p;
    inicializar(&p);
    for (int i = 0; str[i] != '\0'; i++) {
        char c = str[i];
        if (c == '(' || c == '{' || c == '[') push(&p, c);
        else if (c == ')' || c == '}' || c == ']') {
            if (esta_vazia(&p)) return 0;
            char t = pop(&p);
            if ((c == ')' && t != '(') ||
                (c == '}' && t != '{') ||
                (c == ']' && t != '[')) return 0;
        }
    }
    return esta_vazia(&p);
}

int main() {
    printf("%d\n", verificar_balanceamento("({[]})"));
    printf("%d\n", verificar_balanceamento("({[})"));
    return 0;
}

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct {
    char* dados;
    int topo;
    int capacidade;
} Pilha;

void pilha_inicializar(Pilha* p, int tamanho) {
    p->dados = malloc(tamanho * sizeof(char));
    p->topo = -1;
    p->capacidade = tamanho;
}

void pilha_push(Pilha* p, char c) {
    if (p->topo < p->capacidade - 1) p->dados[++(p->topo)] = c;
}

char pilha_pop(Pilha* p) {
    if (p->topo == -1) return '\0';
    return p->dados[(p->topo)--];
}

int pilha_vazia(Pilha* p) {
    return p->topo == -1;
}

void inverter_string(char* str) {
    int n = strlen(str);
    Pilha p;
    pilha_inicializar(&p, n);
    for (int i = 0; i < n; i++) pilha_push(&p, str[i]);
    for (int i = 0; i < n; i++) str[i] = pilha_pop(&p);
    free(p.dados);
}

int main() {
    char str[] = "hello";
    inverter_string(str);
    printf("%s\n", str);
    return 0;
}

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct {
    char* dados;
    int topo;
    int capacidade;
} Pilha;

void pilha_inicializar(Pilha* p, int tamanho) {
    p->dados = malloc(tamanho * sizeof(char));
    p->topo = -1;
    p->capacidade = tamanho;
}

void pilha_push(Pilha* p, char c) {
    if (p->topo < p->capacidade - 1) p->dados[++(p->topo)] = c;
}

char pilha_pop(Pilha* p) {
    if (p->topo == -1) return '\0';
    return p->dados[(p->topo)--];
}

int pilha_vazia(Pilha* p) {
    return p->topo == -1;
}

int eh_palindromo(char* str) {
    int n = strlen(str);
    Pilha p;
    pilha_inicializar(&p, n);
    for (int i = 0; i < n / 2; i++) pilha_push(&p, str[i]);
    int start = (n % 2 == 0) ? n / 2 : n / 2 + 1;
    for (int i = start; i < n; i++) {
        if (pilha_pop(&p) != str[i]) {
            free(p.dados);
            return 0;
        }
    }
    free(p.dados);
    return 1;
}

int main() {
    printf("%d\n", eh_palindromo("radar"));
    printf("%d\n", eh_palindromo("hello"));
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int* dados;
    int topo;
    int capacidade;
} Pilha;

void pilha_inicializar(Pilha* p, int tamanho) {
    p->dados = malloc(tamanho * sizeof(int));
    p->topo = -1;
    p->capacidade = tamanho;
}

void pilha_push(Pilha* p, int valor) {
    if (p->topo < p->capacidade - 1) p->dados[++(p->topo)] = valor;
}

int pilha_pop(Pilha* p) {
    if (p->topo == -1) return -1;
    return p->dados[(p->topo)--];
}

int pilha_vazia(Pilha* p) {
    return p->topo == -1;
}

int pilha_topo(Pilha* p) {
    if (p->topo == -1) return -1;
    return p->dados[p->topo];
}

void ordenar_pilha(Pilha* p) {
    Pilha aux;
    pilha_inicializar(&aux, p->capacidade);
    while (!pilha_vazia(p)) {
        int temp = pilha_pop(p);
        while (!pilha_vazia(&aux) && pilha_topo(&aux) > temp) {
            pilha_push(p, pilha_pop(&aux));
        }
        pilha_push(&aux, temp);
    }
    while (!pilha_vazia(&aux)) pilha_push(p, pilha_pop(&aux));
}

int main() {
    Pilha p;
    pilha_inicializar(&p, 10);
    pilha_push(&p, 3);
    pilha_push(&p, 1);
    pilha_push(&p, 4);
    pilha_push(&p, 2);
    ordenar_pilha(&p);
    while (!pilha_vazia(&p)) printf("%d ", pilha_pop(&p));
    printf("\n");
    free(p.dados);
    return 0;
}

#include <stdio.h>

#define MAX 100

typedef struct {
    int dados[MAX];
    int inicio, fim, tamanho;
} Fila;

void inicializar(Fila* f) {
    f->inicio = 0;
    f->fim = -1;
    f->tamanho = 0;
}

int enfileirar(Fila* f, int valor) {
    if (f->tamanho == MAX) return 0;
    f->fim = (f->fim + 1) % MAX;
    f->dados[f->fim] = valor;
    f->tamanho++;
    return 1;
}

int desenfileirar(Fila* f) {
    if (f->tamanho == 0) return -1;
    int valor = f->dados[f->inicio];
    f->inicio = (f->inicio + 1) % MAX;
    f->tamanho--;
    return valor;
}

int frente(Fila* f) {
    if (f->tamanho == 0) return -1;
    return f->dados[f->inicio];
}

int main() {
    Fila f;
    inicializar(&f);
    enfileirar(&f, 10);
    enfileirar(&f, 20);
    printf("%d\n", frente(&f));
    printf("%d\n", desenfileirar(&f));
    printf("%d\n", desenfileirar(&f));
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

typedef struct {
    No* inicio;
    No* fim;
} Fila;

void inicializar(Fila* f) {
    f->inicio = NULL;
    f->fim = NULL;
}

void enfileirar(Fila* f, int valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = valor;
    novo->prox = NULL;
    if (f->fim == NULL) {
        f->inicio = novo;
        f->fim = novo;
    } else {
        f->fim->prox = novo;
        f->fim = novo;
    }
}

int desenfileirar(Fila* f) {
    if (f->inicio == NULL) return -1;
    No* temp = f->inicio;
    int valor = temp->valor;
    f->inicio = f->inicio->prox;
    if (f->inicio == NULL) f->fim = NULL;
    free(temp);
    return valor;
}

int frente(Fila* f) {
    if (f->inicio == NULL) return -1;
    return f->inicio->valor;
}

int main() {
    Fila f;
    inicializar(&f);
    enfileirar(&f, 10);
    enfileirar(&f, 20);
    printf("%d\n", frente(&f));
    printf("%d\n", desenfileirar(&f));
    printf("%d\n", desenfileirar(&f));
    return 0;
}

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct No {
    char* valor;
    struct No* prox;
} No;

typedef struct {
    No* inicio;
    No* fim;
} Fila;

void inicializar(Fila* f) {
    f->inicio = NULL;
    f->fim = NULL;
}

void enfileirar(Fila* f, char* valor) {
    No* novo = malloc(sizeof(No));
    novo->valor = strdup(valor);
    novo->prox = NULL;
    if (f->fim == NULL) {
        f->inicio = novo;
        f->fim = novo;
    } else {
        f->fim->prox = novo;
        f->fim = novo;
    }
}

char* desenfileirar(Fila* f) {
    if (f->inicio == NULL) return NULL;
    No* temp = f->inicio;
    char* valor = temp->valor;
    f->inicio = f->inicio->prox;
    if (f->inicio == NULL) f->fim = NULL;
    free(temp);
    return valor;
}

void gerar_binarios(int n) {
    Fila f;
    inicializar(&f);
    enfileirar(&f, "1");
    for (int i = 0; i < n; i++) {
        char* s = desenfileirar(&f);
        printf("%s\n", s);
        char s0[100], s1[100];
        snprintf(s0, sizeof(s0), "%s0", s);
        snprintf(s1, sizeof(s1), "%s1", s);
        enfileirar(&f, s0);
        enfileirar(&f, s1);
        free(s);
    }
}

int main() {
    gerar_binarios(10);
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

typedef struct {
    int dados[MAX];
    int inicio, fim, tamanho;
} Fila;

void inicializar(Fila* f) {
    f->inicio = 0;
    f->fim = -1;
    f->tamanho = 0;
}

int enfileirar(Fila* f, int valor) {
    if (f->tamanho == MAX) return 0;
    f->fim = (f->fim + 1) % MAX;
    f->dados[f->fim] = valor;
    f->tamanho++;
    return 1;
}

int desenfileirar(Fila* f) {
    if (f->tamanho == 0) return -1;
    int valor = f->dados[f->inicio];
    f->inicio = (f->inicio + 1) % MAX;
    f->tamanho--;
    return valor;
}

void inverter_primeiros_k(Fila* f, int k) {
    if (k > f->tamanho) return;
    int pilha[MAX];
    int topo = -1;
    for (int i = 0; i < k; i++) {
        pilha[++topo] = desenfileirar(f);
    }
    while (topo >= 0) {
        enfileirar(f, pilha[topo--]);
    }
    int tamanho_restante = f->tamanho - k;
    for (int i = 0; i < tamanho_restante; i++) {
        enfileirar(f, desenfileirar(f));
    }
}

void imprimir_fila(Fila* f) {
    int i = f->inicio;
    for (int count = 0; count < f->tamanho; count++) {
        printf("%d ", f->dados[i]);
        i = (i + 1) % MAX;
    }
    printf("\n");
}

int main() {
    Fila f;
    inicializar(&f);
    for (int i = 1; i <= 5; i++) enfileirar(&f, i);
    inverter_primeiros_k(&f, 3);
    imprimir_fila(&f);
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

int detectar_ciclo(No* head) {
    No *lento = head, *rapido = head;
    while (rapido != NULL && rapido->prox != NULL) {
        lento = lento->prox;
        rapido = rapido->prox->prox;
        if (lento == rapido) return 1;
    }
    return 0;
}

int main() {
    No* a = malloc(sizeof(No));
    No* b = malloc(sizeof(No));
    No* c = malloc(sizeof(No));
    a->valor = 1; a->prox = b;
    b->valor = 2; b->prox = c;
    c->valor = 3; c->prox = b; // ciclo
    printf("%d\n", detectar_ciclo(a));
    c->prox = NULL; // remove ciclo
    printf("%d\n", detectar_ciclo(a));
    free(a); free(b); free(c);
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

No* unir_listas_ordenadas(No* l1, No* l2) {
    No dummy;
    No* atual = &dummy;
    dummy.prox = NULL;
    while (l1 && l2) {
        if (l1->valor < l2->valor) {
            atual->prox = l1;
            l1 = l1->prox;
        } else {
            atual->prox = l2;
            l2 = l2->prox;
        }
        atual = atual->prox;
    }
    atual->prox = (l1 != NULL) ? l1 : l2;
    return dummy.prox;
}

void imprimir(No* head) {
    while (head) {
        printf("%d ", head->valor);
        head = head->prox;
    }
    printf("\n");
}

int main() {
    No a = {1, NULL}, b = {3, NULL}, c = {5, NULL};
    a.prox = &b; b.prox = &c;
    No x = {2, NULL}, y = {4, NULL}, z = {6, NULL};
    x.prox = &y; y.prox = &z;
    No* nova = unir_listas_ordenadas(&a, &x);
    imprimir(nova);
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

No* remover_todas_ocorrencias(No* head, int val) {
    while (head && head->valor == val) {
        No* temp = head;
        head = head->prox;
        free(temp);
    }
    No* atual = head;
    while (atual && atual->prox) {
        if (atual->prox->valor == val) {
            No* temp = atual->prox;
            atual->prox = temp->prox;
            free(temp);
        } else {
            atual = atual->prox;
        }
    }
    return head;
}

void imprimir(No* head) {
    while (head) {
        printf("%d ", head->valor);
        head = head->prox;
    }
    printf("\n");
}

int main() {
    No* a = malloc(sizeof(No));
    No* b = malloc(sizeof(No));
    No* c = malloc(sizeof(No));
    a->valor = 1; a->prox = b;
    b->valor = 2; b->prox = c;
    c->valor = 1; c->prox = NULL;
    No* nova = remover_todas_ocorrencias(a, 1);
    imprimir(nova);
    // liberar memória omitido para brevidade
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

int tamanho(No* head) {
    int cont = 0;
    while (head) {
        cont++;
        head = head->prox;
    }
    return cont;
}

No* encontrar_intersecao(No* l1, No* l2) {
    int t1 = tamanho(l1);
    int t2 = tamanho(l2);
    while (t1 > t2) {
        l1 = l1->prox;
        t1--;
    }
    while (t2 > t1) {
        l2 = l2->prox;
        t2--;
    }
    while (l1 && l2) {
        if (l1 == l2) return l1;
        l1 = l1->prox;
        l2 = l2->prox;
    }
    return NULL;
}

int main() {
    No* a = malloc(sizeof(No));
    No* b = malloc(sizeof(No));
    No* c = malloc(sizeof(No));
    a->valor = 1; a->prox = b;
    b->valor = 2; b->prox = c;
    c->valor = 3; c->prox = NULL;
    No* x = malloc(sizeof(No));
    x->valor = 4; x->prox = c;
    No* inter = encontrar_intersecao(a, x);
    if (inter) printf("Intersecao: %d\n", inter->valor);
    else printf("Sem intersecao\n");
    free(a); free(b); free(c); free(x);
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

No* rotacionar_lista(No* head, int k) {
    if (!head || k == 0) return head;
    No* atual = head;
    int tamanho = 1;
    while (atual->prox) {
        atual = atual->prox;
        tamanho++;
    }
    atual->prox = head;
    k = k % tamanho;
    int passos = tamanho - k;
    while (passos--) {
        atual = atual->prox;
    }
    head = atual->prox;
    atual->prox = NULL;
    return head;
}

void imprimir(No* head) {
    while (head) {
        printf("%d ", head->valor);
        head = head->prox;
    }
    printf("\n");
}

int main() {
    No a = {1, NULL}, b = {2, NULL}, c = {3, NULL}, d = {4, NULL}, e = {5, NULL};
    a.prox = &b; b.prox = &c; c.prox = &d; d.prox = &e;
    No* nova = rotacionar_lista(&a, 2);
    imprimir(nova);
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int* dados;
    int* minimos;
    int topo;
    int capacidade;
} Pilha;

void pilha_inicializar(Pilha* p, int capacidade) {
    p->dados = malloc(capacidade * sizeof(int));
    p->minimos = malloc(capacidade * sizeof(int));
    p->topo = -1;
    p->capacidade = capacidade;
}

void pilha_push(Pilha* p, int val) {
    if (p->topo == p->capacidade - 1) return;
    p->topo++;
    p->dados[p->topo] = val;
    if (p->topo == 0) p->minimos[p->topo] = val;
    else p->minimos[p->topo] = (val < p->minimos[p->topo - 1]) ? val : p->minimos[p->topo - 1];
}

void pilha_pop(Pilha* p) {
    if (p->topo == -1) return;
    p->topo--;
}

int pilha_topo(Pilha* p) {
    if (p->topo == -1) return -1;
    return p->dados[p->topo];
}

int obter_minimo(Pilha* p) {
    if (p->topo == -1) return -1;
    return p->minimos[p->topo];
}

int main() {
    Pilha p;
    pilha_inicializar(&p, 10);
    pilha_push(&p, 5);
    pilha_push(&p, 3);
    pilha_push(&p, 7);
    printf("Minimo: %d\n", obter_minimo(&p));
    pilha_pop(&p);
    printf("Minimo: %d\n", obter_minimo(&p));
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

typedef struct {
    int dados[MAX];
    int topo1, topo2;
} DuasPilhas;

void inicializar(DuasPilhas* dp) {
    dp->topo1 = -1;
    dp->topo2 = MAX;
}

void push1(DuasPilhas* dp, int val) {
    if (dp->topo1 + 1 == dp->topo2) return; // cheio
    dp->dados[++dp->topo1] = val;
}

void push2(DuasPilhas* dp, int val) {
    if (dp->topo1 + 1 == dp->topo2) return; // cheio
    dp->dados[--dp->topo2] = val;
}

int pop1(DuasPilhas* dp) {
    if (dp->topo1 == -1) return -1;
    return dp->dados[dp->topo1--];
}

int pop2(DuasPilhas* dp) {
    if (dp->topo2 == MAX) return -1;
    return dp->dados[dp->topo2++];
}

int main() {
    DuasPilhas dp;
    inicializar(&dp);
    push1(&dp, 10);
    push2(&dp, 20);
    push1(&dp, 30);
    printf("%d %d\n", pop1(&dp), pop2(&dp));
    return 0;
}

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>

#define MAX 100

typedef struct {
    int dados[MAX];
    int topo;
} Pilha;

void push(Pilha* p, int val) {
    p->dados[++p->topo] = val;
}

int pop(Pilha* p) {
    return p->dados[p->topo--];
}

int avaliar_posfixa(const char* expr) {
    Pilha p = {.topo = -1};
    int i = 0, n = strlen(expr);
    while (i < n) {
        if (isspace(expr[i])) { i++; continue; }
        if (isdigit(expr[i])) {
            int val = 0;
            while (i < n && isdigit(expr[i])) {
                val = val * 10 + (expr[i] - '0');
                i++;
            }
            push(&p, val);
        } else {
            int b = pop(&p);
            int a = pop(&p);
            switch (expr[i]) {
                case '+': push(&p, a + b); break;
                case '-': push(&p, a - b); break;
                case '*': push(&p, a * b); break;
                case '/': push(&p, a / b); break;
            }
            i++;
        }
    }
    return pop(&p);
}

int main() {
    printf("%d\n", avaliar_posfixa("3 4 + 2 *"));
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

typedef struct {
    int dados[MAX];
    int topo;
} Pilha;

void push(Pilha* p, int val) {
    p->dados[++p->topo] = val;
}

int pop(Pilha* p) {
    return p->dados[p->topo--];
}

typedef struct {
    Pilha s1, s2;
} Fila;

void fila_inicializar(Fila* f) {
    f->s1.topo = -1;
    f->s2.topo = -1;
}

void enfileirar(Fila* f, int val) {
    push(&f->s1, val);
}

int desenfileirar(Fila* f) {
    if (f->s2.topo == -1) {
        while (f->s1.topo != -1) {
            push(&f->s2, pop(&f->s1));
        }
    }
    if (f->s2.topo == -1) return -1;
    return pop(&f->s2);
}

int main() {
    Fila f;
    fila_inicializar(&f);
    enfileirar(&f, 10);
    enfileirar(&f, 20);
    printf("%d\n", desenfileirar(&f));
    printf("%d\n", desenfileirar(&f));
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

No* inverter_grupo(No* head, int k, No** prox_grupo) {
    No* prev = NULL;
    No* curr = head;
    int count = 0;
    while (curr && count < k) {
        No* next = curr->prox;
        curr->prox = prev;
        prev = curr;
        curr = next;
        count++;
    }
    *prox_grupo = curr;
    return prev;
}

No* inverter_grupos(No* head, int k) {
    if (!head || k == 1) return head;
    No* novo_head = NULL;
    No* prev_fim = NULL;
    No* atual = head;

    while (atual) {
        No* prox_grupo = NULL;
        No* inicio = atual;
        No* fim = inverter_grupo(atual, k, &prox_grupo);
        if (!novo_head) novo_head = fim;
        if (prev_fim) prev_fim->prox = fim;
        prev_fim = inicio;
        atual = prox_grupo;
    }
    return novo_head;
}

void imprimir(No* head) {
    while (head) {
        printf("%d ", head->valor);
        head = head->prox;
    }
    printf("\n");
}

int main() {
    No nos[5];
    for (int i = 0; i < 5; i++) {
        nos[i].valor = i + 1;
        nos[i].prox = (i < 4) ? &nos[i+1] : NULL;
    }
    No* nova = inverter_grupos(&nos[0], 2);
    imprimir(nova);
    return 0;
}

#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No* prox;
} No;

No* inverter(No* head) {
    No* prev = NULL;
    No* curr = head;
    while (curr) {
        No* next = curr->prox;
        curr->prox = prev;
        prev = curr;
        curr = next;
    }
    return prev;
}

int eh_palindromo(No* head) {
    if (!head || !head->prox) return 1;
    No* lento = head;
    No* rapido = head;
    while (rapido->prox && rapido->prox->prox) {
        lento = lento->prox;
        rapido = rapido->prox->prox;
    }
    No* segunda_metade = inverter(lento->prox);
    No* inicio_segunda = segunda_metade;
    No* p1 = head;
    int palindromo = 1;
    while (segunda_metade) {
        if (p1->valor != segunda_metade->valor) {
            palindromo = 0;
            break;
        }
        p1 = p1->prox;
        segunda_metade = segunda_metade->prox;
    }
    lento->prox = inverter(inicio_segunda);
    return palindromo;
}

int main() {
    No nos[5] = {{1,NULL},{2,NULL},{3,NULL},{2,NULL},{1,NULL}};
    for (int i = 0; i < 4; i++) nos[i].prox = &nos[i+1];
    printf("%d\n", eh_palindromo(&nos[0]));
    nos[2].valor = 4;
    printf("%d\n", eh_palindromo(&nos[0]));
    return 0;
}

#include <stdio.h>

int trapping_rain_water(int* heights, int n) {
    int stack[n];
    int topo = -1;
    int i = 0, resultado = 0;
    while (i < n) {
        while (topo != -1 && heights[i] > heights[stack[topo]]) {
            int base = stack[topo--];
            if (topo == -1) break;
            int dist = i - stack[topo] -1;
            int altura = (heights[i] < heights[stack[topo]] ? heights[i] : heights[stack[topo]]) - heights[base];
            resultado += dist * altura;
        }
        stack[++topo] = i++;
    }
    return resultado;
}

int main() {
    int barras[] = {0,1,0,2,1,0,1,3,2,1,2,1};
    int n = sizeof(barras)/sizeof(barras[0]);
    printf("%d\n", trapping_rain_water(barras, n));
    return 0;
}
