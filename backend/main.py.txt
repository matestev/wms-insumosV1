from fastapi import FastAPI
from fastapi.middleware.cors import CORSMiddleware

app = FastAPI()

origins = ["*"]

app.add_middleware(
    CORSMiddleware,
    allow_origins=origins,
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

@app.post("/login")
async def login(username: str, password: str):
    if username == "admin" and password == "1234":
        return {"status": "ok"}
    return {"status": "fail"}

@app.post("/gerar_lpn")
async def gerar_lpn(data: dict):
    return {"arquivo_gerado": True}
