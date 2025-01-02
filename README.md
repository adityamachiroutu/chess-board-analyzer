# chessboard-analyzer

## Overview

This project is a Chessboard Analyzer that uses a picture of a physical chessboard to suggest the best move. The system combines YOLO for image analysis to detect the chessboard and pieces, and Stockfish as the chess engine to calculate the best move.

## Features

- Detects chessboard and pieces from a physical chessboard image.
- Recognizes board state and converts it to FEN (Forsyth-Edwards Notation).
- Suggests the best move using Stockfish.
- Supports all chess rules including castling, en passant, and pawn promotion.
- (Optional) Provides a visual overlay of the suggested move on the input image.

## Project Structure

```
chessboard-analyzer/
├── data/                 # Dataset for YOLO training
├── models/               # YOLO trained weights
├── src/                  # Source code
│   ├── detect.py         # YOLO-based detection
│   ├── board_mapping.py  # Mapping YOLO output to chessboard squares
│   ├── fen_generator.py  # Convert board state to FEN
│   ├── stockfish.py      # Interface with Stockfish
│   └── main.py           # Main script to combine all steps
├── requirements.txt      # Python dependencies
└── README.md             # Project documentation
```

## Installation

### Prerequisites

- Python 3.8 or later
- A working camera (webcam or phone camera)

### Steps

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/chessboard-analyzer.git
   cd chessboard-analyzer
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Download and set up Stockfish:
   - Visit [Stockfish Download Page](https://stockfishchess.org/download/).
   - Place the Stockfish binary in the `src/` directory.
4. Download or train a YOLO model:
   - Use the pre-trained YOLO weights provided in `models/`.
   - Alternatively, train your own model using the dataset in `data/`.

## Usage

1. Capture an image of the chessboard:
   - Ensure the board is well-lit and the camera captures the full board.
2. Run the analyzer:
   ```bash
   python src/main.py --image path/to/image.jpg
   ```
3. View the suggested move:
   - The move will be printed in chess notation (e.g., `e2e4`).
   - (Optional) The output image with the suggested move highlighted will be saved.

## Workflow

1. **Image Capture:** A picture of the chessboard is provided as input.
2. **Piece Detection:** YOLO detects pieces and their positions on the board.
3. **Board Mapping:** The detected pieces are mapped to squares (e.g., `a1`, `h8`).
4. **FEN Generation:** The board state is converted to a FEN string.
5. **Move Suggestion:** The FEN is passed to Stockfish, which calculates the best move.

## Example

### Input:

An image of a chessboard.

### Output:

- Suggested move: `e2e4`
- Annotated image:

![Example Output](example_output.jpg)

## Future Enhancements

- Improve piece detection under poor lighting conditions.
- Add a graphical user interface (GUI) for ease of use.
- Support video input for real-time move suggestions.

## Contributing

Contributions are welcome! Please submit a pull request or open an issue to discuss your ideas.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgments

- [YOLO](https://github.com/ultralytics/yolov5) for object detection.
- [Stockfish](https://stockfishchess.org/) for chess engine functionality.
- [python-chess](https://github.com/niklasf/python-chess) for chess logic integration.
