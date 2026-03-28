# GenLayer-Audit-Tutorial
An introductory tutorial on building an Intelligent Audit Dispute Resolver using GenLayer's Equivalence Principle.
GenLayer Tutorial: Smart Audit Dispute Resolver
This tutorial demonstrates how to use GenLayer to handle subjective financial disputes that traditional blockchains can't solve.

Key Concept: The Equivalence Principle
In this project, we use GenLayer's AI-driven consensus to compare reports from a Client and an Auditor. If they don't match, the network uses Optimistic Democracy to determine the truth.

from genlayer import *

class AuditContract(Contract):
    def __init__(self):
        self.client_report = ""
        self.auditor_report = ""
        self.status = "Open"

    @public
    def submit_report(self, report_hash: str, role: str):
        if role == "client":
            self.client_report = report_hash
        else:
            self.auditor_report = report_hash
        
        if self.client_report and self.auditor_report and self.client_report != self.auditor_report:
            self.status = "Dispute Detected - Resolving via AI Consensus"
