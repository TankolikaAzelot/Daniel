# Daniel
Programmesana
pip install flask
from flask import Flask, jsonify

app = Flask(__name__)

# Datu avots ar universitāšu informāciju (piemērs)
universities = [
    {"name": "Latvijas Universitāte"},
    {"name": "Rīgas Tehniskā universitāte"},
    {"name": "Daugavpils Universitāte"},
    # ... citu universitāšu informācija ...
]

# API endpoint, kas atgriež Latvijas universitātes sakārtotas alfabētiskā secībā
@app.route('/api/universities', methods=['GET'])
def get_universities():
    latvian_universities = [uni["name"] for uni in universities if "Latvija" in uni["name"]]
    sorted_universities = sorted(latvian_universities)
    return jsonify({"universities": sorted_universities})

if __name__ == '__main__':
    app.run(debug=True)
python app.py
