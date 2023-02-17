import heapq

def find_paths(graph, start, end, mandatory, excluded):
    # Инициализируем список, в который будут добавляться все пути удовлетворяющие условиям
    paths = []
    # Алгоритм Дейкстры
    queue = [(0, start, [start])]
    while queue:
        (cost, node, path) = heapq.heappop(queue)
        if node == end and mandatory in path and excluded not in path:
            paths.append((cost, path))
        for neighbor, weight in graph[node].items():
            if neighbor not in path:
                heapq.heappush(queue, (cost + weight, neighbor, path + [neighbor]))
    return paths


graph1 = {
    'A': {'B': 2, 'C': 4, 'D': 5, 'F': 16},
    'B': {'A': 2, 'D': 3},
    'C': {'A': 4, 'D': 3},
    'D': {'A': 5, 'B': 3, 'C': 3, 'E': 2, 'F': 3},
    'E': {'D': 2, 'F': 8},
    'F': {'A': 16, 'D': 3, 'E': 8}
}

print('Введите аргументы функции через пробел: Начало Конец Обязательная точка Недопустимая точка')
arguments = input().split()
start = arguments[0]
end = arguments[1]
mandatory = arguments[2]
excluded = arguments[3]

paths = find_paths(graph1, start, end, mandatory, excluded)

print("Найденные пути:")
for path in paths:
    print("Путь: ", path[1], "с весом: ", path[0])

if paths:
    shortest_path_weight, shortest_path = min(paths, key=lambda x: x[0])
    print('\nКратчайший путь, содержащий', mandatory, 'и исключающий', excluded, shortest_path, 'с весом', shortest_path_weight)
else:
    print('Ничего не найдено')
