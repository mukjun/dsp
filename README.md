def print_minefield(field):
    N = len(field)  # field의 크기
    # 결과를 저장할 새로운 리스트 생성
    result_field = [['0' for _ in range(N)] for _ in range(N)]

    for row in range(N):
        for col in range(N):
            # 지뢰(1)를 발견하면
            if field[row][col] == 1:
                result_field[row][col] = '*'
                # 주변 8칸을 확인하고 지뢰가 아닌 칸의 숫자를 1씩 증가
                for dx in [-1, 0, 1]:
                    for dy in [-1, 0, 1]:
                        nx, ny = row + dx, col + dy
                        # 범위를 벗어나지 않고, 현재 칸이 지뢰가 아닌 경우
                        if 0 <= nx < N and 0 <= ny < N and field[nx][ny] == 0:
                            result_field[nx][ny] = str(int(result_field[nx][ny]) + 1)

    # 변환된 리스트를 출력
    for row in result_field:
        print(' '.join(row))



example_field = [
    [1, 0, 1, 1],
    [0, 0, 0, 0],
    [1, 0, 1, 0],
    [0, 1, 0, 1]
]

print_minefield(example_field)